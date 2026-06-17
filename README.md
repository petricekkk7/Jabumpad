# Jabumpad
a hackpad from me
used AI just for the firmvare took me like 8hours min  
hardest thing was the PCB 
the tutorial is pretty confusing for me so if i got somting wrong am soory

SCHEMATIC


<img width="811" height="622" alt="PCB" src="https://github.com/user-attachments/assets/8cd79257-6152-43fd-8437-0ac743a63dff" />




THE PCB LAYOUT




<img width="545" height="394" alt="PCB 2" src="https://github.com/user-attachments/assets/d693e73d-5d36-48bb-8ef3-f67d827dd4cc" />




A VIEW OF THE PCB IM 3D VIEWER




<img width="910" height="543" alt="PCB 3" src="https://github.com/user-attachments/assets/a21bb4b8-fb41-4a28-b961-54d8bcc0f4ed" />






THE CASE 




<img width="1329" height="922" alt="CASE" src="https://github.com/user-attachments/assets/af360569-3604-4998-b6c5-e3bdbb82afc1" />



THE FIRMWARE 


import board
from kmk.kmk_keyboard import KMKKeyboard
from kmk.keys import KC
from kmk.scanners import PinsScanner
from kmk.extensions.encoder import Encoder

# Inicializace klávesnice
keyboard = KMKKeyboard()

# 1. MAPOVÁNÍ JEDNOTLIVÝCH PINŮ PRO TLAČÍTKA (Podle schématu)
# SW5 -> pin 9 (PA7_A8_D8_SCK)  -> board.D8
# SW1 -> pin 11 (PA6_A10_D10_MOSI) -> board.D10
# SW2 -> pin 10 (PA5_A9_D9_MISO)  -> board.D9
# SW3 -> pin 6 (PA9_A5_D5_SCL)   -> board.D5
# SW4 (stisk enkodéru, piny S1/S2) -> pin 1 (PA02_A0_D0) -> board.D0
keyboard.matrix = PinsScanner([
    board.D8,   # 1. tlačítko: SW5
    board.D10,  # 2. tlačítko: SW1
    board.D9,   # 3. tlačítko: SW2
    board.D5,   # 4. tlačítko: SW3
    board.D0,   # 5. tlačítko: Stisk enkodéru (SW4)
])

# 2. AKCE PRO TLAČÍTKA (Změňte si klávesy podle libosti)
# Pořadí v seznamu přesně odpovídá pořadí pinů v PinsScanner výše
keyboard.keymap = [
    [
        KC.W,     # SW5 (např. šipka nahoru / W)
        KC.D,     # SW1 (např. doprava / D)
        KC.A,     # SW2 (např. doleva / A)
        KC.S,     # SW3 (např. dolů / S)
        KC.MUTE,  # Stisk enkodéru (Ztlumit zvuk)
    ]
]

# 3. NASTAVENÍ OTÁČENÍ ENKODÉRU (SW4)
# Podle schématu:
# Pin A enkodéru -> pin 2 (PA4_A1_D1) -> board.D1
# Pin B enkodéru -> pin 3 (PA10_A2_D2) -> board.D2
# Pin C enkodéru -> jde na GND
encoder = Encoder()
keyboard.extensions.append(encoder)

encoder.pins = (
    (board.D1, board.D2, (((KC.VOLD, KC.VOLU),),)), # Doleva = Snížit hlasitost, Doprava = Zvýšit hlasitost
)

if __name__ == "__main__":
    keyboard.go()

  
   
If i missed somting am sorry  /import board
from kmk.kmk_keyboard import KMKKeyboard
from kmk.keys import KC
from kmk.scanners import PinsScanner
from kmk.extensions.encoder import Encoder

# Inicializace klávesnice
keyboard = KMKKeyboard()

# 1. MAPOVÁNÍ JEDNOTLIVÝCH PINŮ PRO TLAČÍTKA (Podle schématu)
# SW5 -> pin 9 (PA7_A8_D8_SCK)  -> board.D8
# SW1 -> pin 11 (PA6_A10_D10_MOSI) -> board.D10
# SW2 -> pin 10 (PA5_A9_D9_MISO)  -> board.D9
# SW3 -> pin 6 (PA9_A5_D5_SCL)   -> board.D5
# SW4 (stisk enkodéru, piny S1/S2) -> pin 1 (PA02_A0_D0) -> board.D0
keyboard.matrix = PinsScanner([
    board.D8,   # 1. tlačítko: SW5
    board.D10,  # 2. tlačítko: SW1
    board.D9,   # 3. tlačítko: SW2
    board.D5,   # 4. tlačítko: SW3
    board.D0,   # 5. tlačítko: Stisk enkodéru (SW4)
])

# 2. AKCE PRO TLAČÍTKA (Změňte si klávesy podle libosti)
# Pořadí v seznamu přesně odpovídá pořadí pinů v PinsScanner výše
keyboard.keymap = [
    [
        KC.W,     # SW5 (např. šipka nahoru / W)
        KC.D,     # SW1 (např. doprava / D)
        KC.A,     # SW2 (např. doleva / A)
        KC.S,     # SW3 (např. dolů / S)
        KC.MUTE,  # Stisk enkodéru (Ztlumit zvuk)
    ]
]

# 3. NASTAVENÍ OTÁČENÍ ENKODÉRU (SW4)
# Podle schématu:
# Pin A enkodéru -> pin 2 (PA4_A1_D1) -> board.D1
# Pin B enkodéru -> pin 3 (PA10_A2_D2) -> board.D2
# Pin C enkodéru -> jde na GND
encoder = Encoder()
keyboard.extensions.append(encoder)

encoder.pins = (
    (board.D1, board.D2, (((KC.VOLD, KC.VOLU),),)), # Doleva = Snížit hlasitost, Doprava = Zvýšit hlasitost
)

if __name__ == "__main__":
    keyboard.go()
 
 
 
 
 
    IF I MISSED SOMTING AM SORRY 
