---
title: "Undifined reference to espeak-ng headers in Ubuntu"
date: 2017-10-31
forum: General Help
---

### Post by rezaee on 2017-10-31
I have downloaded `espeak-ng 1.1.49` and `./configure make make install` it, and tested it by `espeak --stdout "this is a test" | paplay` successfully and it worked. Then I tried to use it inside my C++ code(testSpeak.cpp) that I found on the internet as you can see below:

 
```
    #include <string.h>
    #include <vector> 
    #include </usr/local/include/espeak-ng/speak_lib.h> 
    
    int samplerate; // determined by espeak, will be in Hertz (Hz)
    const int buflength = 200; // passed to espeak, in milliseconds (ms)
    
    std::vector<short> sounddata;
    
    int SynthCallback(short *wav, int numsamples, espeak_EVENT *events) {
        if (wav == NULL)
            return 1; // NULL means done.
    
        /* process your samples here, let's just gather them */
        sounddata.insert(sounddata.end(), wav, wav + numsamples);
        return 0; // 0 continues synthesis, 1 aborts 
    }
    
    int main(int argc, char* argv[] ) {
        char text[] = {"my name is espeak"};
        samplerate = espeak_Initialize(AUDIO_OUTPUT_RETRIEVAL, buflength, NULL, 0);
        espeak_SetSynthCallback(&SynthCallback);
        espeak_SetVoiceByName("en"); 
        unsigned int flags=espeakCHARS_AUTO | espeakENDPAUSE;
        size_t size = strlen(text); 
        espeak_Synth(text, size + 1, 0, POS_CHARACTER, 0, flags, NULL, NULL); 
        espeak_Synchronize();
    
        /* in theory sounddata holds your samples now... */
    
        return 0; 
    }
```



But after trying to make executable by this command: `g++ testSpeak.cpp -o speaks` I got these error messages: 
```

    /tmp/ccR9O0vw.o: In function `main':
    testSpeak.cpp:(.text+0x78): undefined reference to `espeak_Initialize'
    testSpeak.cpp:(.text+0x90): undefined reference to `espeak_SetSynthCallback'
    testSpeak.cpp:(.text+0x9c): undefined reference to `espeak_SetVoiceByName'
    testSpeak.cpp:(.text+0xce): undefined reference to `espeak_Synth'
    testSpeak.cpp:(.text+0xd2): undefined reference to `espeak_Synchronize'
    collect2: error: ld returned 1 exit status

```
I know the problem is about linking but as I am new to Linux, don't know how can I fix it! Also I searched a lot but couldn't understand the solutions :(

---

