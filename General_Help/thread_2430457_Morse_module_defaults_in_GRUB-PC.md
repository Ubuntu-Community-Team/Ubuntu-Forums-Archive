---
title: "Morse module defaults in GRUB-PC"
date: 2019-11-02
forum: General Help
---

### Post by bcschmerker on 2019-11-02
**I am currently considering an unconventional configuration of Grand Unified Bootloader** for a pair of older-model Acers under consideration for digital signage in a house of worship.  As intel® had a serious hardware bug in the HD Graphics X4500 that renders the HDMI output unusable (the analog DE-15 renders XGA+ just like the simulation), and I have been unable to obtain more information on a video display adapter usable on the G43T-AM with the stock American Megatrends BIOS in a Gateway DX4822 (the ASUS® EAH6850 DirectCU® was a major fail, not looking right even in power-on self test), I'm seriously considering using the DX4822's internal speaker (driven by a timer in the Super-I/O chip) for monitoring the boot process, as the G43T-AM did not ship with a DE-9 serial port.  Does anybody have a ballpark dot speed for the Morse module that ships with GRUB-PC 2 and later?

---

### Post by norobro on 2019-11-02
[SIZE=2]grub2 sending Morse code is news to me. Anyway my WAG is ~5 WPM. 

I arrived at that by plugging "paris" (11.5 secs.) and "codex" (14 secs.) into the source code.
[https://en.wikipedia.org/wiki/Morse_code#Speed_in_words_per_minute](https://en.wikipedia.org/wiki/Morse_code#Speed_in_words_per_minute)

The source code is here: [http://git.savannah.gnu.org/cgit/grub.git/tree/grub-core/term/morse.c#n19](http://git.savannah.gnu.org/cgit/grub.git/tree/grub-core/term/morse.c#n19)

My code:```
#include <stdio.h>
#include <stdlib.h>

#define BASE_TIME 250
#define DIH 1
#define DAH 3
#define END 0


static const char codes[0x80][6] =
  {
    ['0'] = { DAH, DAH, DAH, DAH, DAH, END },
    ['1'] = { DIH, DAH, DAH, DAH, DAH, END },
    ['2'] = { DIH, DIH, DAH, DAH, DAH, END },
    ['3'] = { DIH, DIH, DIH, DAH, DAH, END },
    ['4'] = { DIH, DIH, DIH, DIH, DAH, END },
    ['5'] = { DIH, DIH, DIH, DIH, DIH, END },
    ['6'] = { DAH, DIH, DIH, DIH, DIH, END },
    ['7'] = { DAH, DAH, DIH, DIH, DIH, END },
    ['8'] = { DAH, DAH, DAH, DIH, DIH, END },
    ['9'] = { DAH, DAH, DAH, DAH, DIH, END },
    ['a'] = { DIH, DAH, END },
    ['b'] = { DAH, DIH, DIH, DIH, END },
    ['c'] = { DAH, DIH, DAH, DIH, END },
    ['d'] = { DAH, DIH, DIH, END },
    ['e'] = { DIH, END },
    ['f'] = { DIH, DIH, DAH, DIH, END },
    ['g'] = { DAH, DAH, DIH, END },
    ['h'] = { DIH, DIH, DIH, DIH, END },
    ['i'] = { DIH, DIH, END },
    ['j'] = { DIH, DAH, DAH, DAH, END },
    ['k'] = { DAH, DIH, DAH, END },
    ['l'] = { DIH, DAH, DIH, DIH, END },
    ['m'] = { DAH, DAH, END },
    ['n'] = { DAH, DIH, END },
    ['o'] = { DAH, DAH, DAH, END },
    ['p'] = { DIH, DAH, DAH, DIH, END },
    ['q'] = { DAH, DAH, DIH, DAH, END },
    ['r'] = { DIH, DAH, DIH, END },
    ['s'] = { DIH, DIH, DIH, END },
    ['t'] = { DAH, END },
    ['u'] = { DIH, DIH, DAH, END },
    ['v'] = { DIH, DIH, DIH, DAH, END },
    ['w'] = { DIH, DAH, DAH, END },
    ['x'] = { DAH, DIH, DIH, DAH, END },
    ['y'] = { DAH, DIH, DAH, DAH, END },
    ['z'] = { DAH, DAH, DIH, DIH, END }
  };


int main(int argc, char *argv[]) {
    if(argc != 2) {
        printf("Usage: ./progname word\n");
        exit(0);
    }
    int total = 0;
    int pos = 0;
    while(argv[1][pos] != '\0') {
        char ch = argv[1][pos];
        for (int i = 0; codes[ch][i]; i++) {
             // printf("%i\n", (codes[ch][i])*BASE_TIME+BASE_TIME); //used for debugging
            total += codes[ch][i]*BASE_TIME+BASE_TIME;
        }
         // printf("\n%i\n", 2*BASE_TIME); //used for debugging
        total += 2*BASE_TIME;
         // printf("\n");
        ++pos;
    }
    printf("Time to send %s = %i milliseconds\n", argv[1], total);
}
```
HTH[/SIZE]

---

