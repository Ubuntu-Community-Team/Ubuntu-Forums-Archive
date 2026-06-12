---
title: "sfxr install help"
date: 2007-12-18
forum: General Help
---

### Post by Ink-Jet on 2007-12-18
Hello

I've been trying to install the sfxr program, by ludum dare
( [http://www.imitationpickles.org/ludum/2007/12/13/sfxr-sound-effects-for-all/](http://www.imitationpickles.org/ludum/2007/12/13/sfxr-sound-effects-for-all/) )
using the linux version.

I save it, extract it, cd into it, and type make, as the instructions say to.
However, it doesn't install.

```
joe@joe-laptop:~/Tech/Applications/sfxr$ make
g++ -ggdb `sdl-config --cflags` `pkg-config gtk+-2.0 --cflags` `sdl-config --libs` `pkg-config gtk+-2.0 --libs` main.cpp -o sfxr
/bin/sh: sdl-config: not found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
/bin/sh: sdl-config: not found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
In file included from main.cpp:11:
sdlkit.h:4:17: error: SDL.h: No such file or directory
sdlkit.h:93:21: error: gtk/gtk.h: No such file or directory
sdlkit.h: In function ‘void error(const char*, unsigned int, const char*)’:
sdlkit.h:13: error: ‘exit’ was not declared in this scope
sdlkit.h: At global scope:
sdlkit.h:16: error: ‘Uint32’ does not name a type
sdlkit.h:17: error: ‘Uint16’ does not name a type
sdlkit.h:28: error: ‘SDLK_LAST’ was not declared in this scope
sdlkit.h:40: error: ‘SDLKey’ has not been declared
sdlkit.h: In static member function ‘static bool DPInput::KeyPressed(int)’:
sdlkit.h:42: error: ‘keys’ was not declared in this scope
sdlkit.h: At global scope:
sdlkit.h:49: error: expected initializer before ‘*’ token
sdlkit.h:50: error: expected initializer before ‘*’ token
sdlkit.h:56: error: expected initializer before ‘*’ token
sdlkit.h: In function ‘void sdlupdate()’:
sdlkit.h:62: error: ‘Uint8’ was not declared in this scope
sdlkit.h:62: error: expected `;' before ‘buttons’
sdlkit.h:66: error: ‘buttons’ was not declared in this scope
sdlkit.h:66: error: ‘SDL_BUTTON’ was not declared in this scope
sdlkit.h: In function ‘bool ddkLock()’:
sdlkit.h:76: error: ‘sdlscreen’ was not declared in this scope
sdlkit.h:76: error: ‘SDL_LockSurface’ was not declared in this scope
sdlkit.h:78: error: ‘ddkscreen16’ was not declared in this scope
sdlkit.h:78: error: ‘Uint16’ was not declared in this scope
sdlkit.h:78: error: expected primary-expression before ‘)’ token
sdlkit.h:79: error: ‘ddkscreen32’ was not declared in this scope
sdlkit.h:79: error: ‘Uint32’ was not declared in this scope
sdlkit.h:79: error: expected primary-expression before ‘)’ token
sdlkit.h: In function ‘void ddkUnlock()’:
sdlkit.h:84: error: ‘sdlscreen’ was not declared in this scope
sdlkit.h:84: error: ‘SDL_UnlockSurface’ was not declared in this scope
sdlkit.h: In function ‘void ddkSetMode(int, int, int, int, int, const char*)’:
sdlkit.h:89: error: ‘sdlscreen’ was not declared in this scope
sdlkit.h:89: error: ‘SDL_FULLSCREEN’ was not declared in this scope
sdlkit.h:89: error: ‘SDL_SetVideoMode’ was not declared in this scope
sdlkit.h:90: error: ‘SDL_WM_SetCaption’ was not declared in this scope
sdlkit.h: At global scope:
sdlkit.h:99: error: variable or field ‘selected_file’ declared void
sdlkit.h:99: error: ‘GtkWidget’ was not declared in this scope
sdlkit.h:99: error: ‘button’ was not declared in this scope
sdlkit.h:99: error: ‘GtkFileSelection’ was not declared in this scope
sdlkit.h:99: error: ‘fs’ was not declared in this scope
sdlkit.h:99: error: initializer expression list treated as compound expression
sdlkit.h:100: error: expected ‘,’ or ‘;’ before ‘{’ token
sdlkit.h: In function ‘bool select_file(char*)’:
sdlkit.h:110: error: ‘GtkWidget’ was not declared in this scope
sdlkit.h:110: error: ‘dialog’ was not declared in this scope
sdlkit.h:110: error: ‘gtk_file_selection_new’ was not declared in this scope
sdlkit.h:111: error: ‘G_OBJECT’ was not declared in this scope
sdlkit.h:111: error: ‘gtk_main_quit’ was not declared in this scope
sdlkit.h:111: error: ‘G_CALLBACK’ was not declared in this scope
sdlkit.h:111: error: ‘g_signal_connect’ was not declared in this scope
sdlkit.h:112: error: ‘GTK_FILE_SELECTION’ was not declared in this scope
sdlkit.h:113: error: ‘gtk_widget_destroy’ was not declared in this scope
sdlkit.h:113: error: ‘g_signal_connect_swapped’ was not declared in this scope
sdlkit.h:114: error: ‘GTK_WIDGET’ was not declared in this scope
sdlkit.h:114: error: ‘gtk_widget_show’ was not declared in this scope
sdlkit.h:115: error: ‘gtk_main’ was not declared in this scope
sdlkit.h: In function ‘void sdlquit()’:
sdlkit.h:125: error: ‘SDL_Quit’ was not declared in this scope
sdlkit.h: In function ‘void sdlinit()’:
sdlkit.h:130: error: ‘SDL_INIT_VIDEO’ was not declared in this scope
sdlkit.h:130: error: ‘SDL_INIT_AUDIO’ was not declared in this scope
sdlkit.h:130: error: ‘SDL_Init’ was not declared in this scope
sdlkit.h:131: error: ‘atexit’ was not declared in this scope
sdlkit.h:132: error: ‘keys’ was not declared in this scope
sdlkit.h: In function ‘void loop()’:
sdlkit.h:138: error: ‘SDL_Event’ was not declared in this scope
sdlkit.h:138: error: expected `;' before ‘e’
sdlkit.h:141: error: ‘e’ was not declared in this scope
sdlkit.h:141: error: ‘SDL_PollEvent’ was not declared in this scope
sdlkit.h:144: error: ‘SDL_QUIT’ was not declared in this scope
sdlkit.h:147: error: ‘SDL_KEYDOWN’ was not declared in this scope
sdlkit.h:148: error: ‘keys’ was not declared in this scope
sdlkit.h:155: error: ‘sdlscreen’ was not declared in this scope
sdlkit.h:155: error: ‘SDL_Flip’ was not declared in this scope
sdlkit.h: In function ‘int main(int, char**)’:
sdlkit.h:161: error: ‘gtk_init’ was not declared in this scope
main.cpp: At global scope:
main.cpp:37: error: ISO C++ forbids declaration of ‘DWORD’ with no type
main.cpp:37: error: expected ‘;’ before ‘*’ token
main.cpp:539: error: ‘Uint8’ has not been declared
main.cpp: In function ‘void SDLAudioCallback(void*, int*, int)’:
main.cpp:552: error: ‘Sint16’ was not declared in this scope
main.cpp:552: error: expected primary-expression before ‘)’ token
main.cpp:552: error: expected `)' before ‘stream’
tools.h: In function ‘void LoadTGA(Spriteset&, const char*)’:
tools.h:18: error: ‘struct Spriteset’ has no member named ‘data’
tools.h:18: error: ‘DWORD’ was not declared in this scope
tools.h:18: error: expected primary-expression before ‘)’ token
tools.h:18: error: expected `;' before ‘malloc’
tools.h:22: error: expected `;' before ‘pixel’
tools.h:24: error: ‘pixel’ was not declared in this scope
tools.h:29: error: ‘struct Spriteset’ has no member named ‘data’
tools.h: At global scope:
tools.h:37: error: variable or field ‘ClearScreen’ declared void
tools.h:37: error: ‘DWORD’ was not declared in this scope
tools.h:38: error: expected ‘,’ or ‘;’ before ‘{’ token
tools.h:56: error: ‘DWORD’ has not been declared
tools.h: In function ‘void DrawBar(int, int, int, int, int)’:
tools.h:65: error: ‘ddkscreen32’ was not declared in this scope
tools.h:75: error: ‘ddkscreen32’ was not declared in this scope
tools.h: At global scope:
tools.h:79: error: ‘DWORD’ has not been declared
tools.h:87: error: ‘DWORD’ has not been declared
tools.h: In function ‘void DrawSprite(Spriteset&, int, int, int, int)’:
tools.h:96: error: ‘DWORD’ was not declared in this scope
tools.h:96: error: expected `;' before ‘p’
tools.h:97: error: ‘p’ was not declared in this scope
tools.h:98: error: ‘ddkscreen32’ was not declared in this scope
tools.h:103: error: ‘DWORD’ was not declared in this scope
tools.h:103: error: expected `;' before ‘p’
tools.h:104: error: ‘p’ was not declared in this scope
tools.h:105: error: ‘ddkscreen32’ was not declared in this scope
tools.h: At global scope:
tools.h:110: error: ‘DWORD’ has not been declared
main.cpp: In function ‘void Slider(int, int, float&, bool, const char*)’:
main.cpp:658: error: ‘DWORD’ was not declared in this scope
main.cpp:658: error: expected `;' before ‘tcol’
main.cpp:660: error: ‘tcol’ was not declared in this scope
main.cpp:661: error: ‘tcol’ was not declared in this scope
main.cpp: In function ‘bool Button(int, int, bool, const char*, int)’:
main.cpp:666: error: ‘DWORD’ was not declared in this scope
main.cpp:666: error: expected `;' before ‘color1’
main.cpp:667: error: expected `;' before ‘color2’
main.cpp:668: error: expected `;' before ‘color3’
main.cpp:675: error: ‘color1’ was not declared in this scope
main.cpp:676: error: ‘color2’ was not declared in this scope
main.cpp:677: error: ‘color3’ was not declared in this scope
main.cpp:681: error: ‘color1’ was not declared in this scope
main.cpp:682: error: ‘color2’ was not declared in this scope
main.cpp:683: error: ‘color3’ was not declared in this scope
main.cpp:685: error: ‘color1’ was not declared in this scope
main.cpp:686: error: ‘color2’ was not declared in this scope
main.cpp:687: error: ‘color3’ was not declared in this scope
main.cpp: In function ‘void DrawScreen()’:
main.cpp:731: error: ‘ClearScreen’ cannot be used as a function
main.cpp: In function ‘bool ddkCalcFrame()’:
main.cpp:1106: error: ‘SDLK_SPACE’ was not declared in this scope
main.cpp:1106: error: ‘SDLK_RETURN’ was not declared in this scope
main.cpp:1119: error: ‘SDL_Delay’ was not declared in this scope
main.cpp: In function ‘void ddkInit()’:
main.cpp:1161: error: ‘SDL_AudioSpec’ was not declared in this scope
main.cpp:1161: error: expected `;' before ‘des’
main.cpp:1162: error: ‘des’ was not declared in this scope
main.cpp:1163: error: ‘AUDIO_S16SYS’ was not declared in this scope
main.cpp:1167: error: ‘SDL_OpenAudio’ was not declared in this scope
main.cpp:1168: error: ‘SDL_PauseAudio’ was not declared in this scope
main.cpp: In function ‘void ddkFree()’:
main.cpp:1175: error: ‘struct Spriteset’ has no member named ‘data’
main.cpp:1176: error: ‘struct Spriteset’ has no member named ‘data’
make: *** [sfxr] Error 1
```

I have tried to apt-get for gtk, and some other items, but to no avail.

Any clues on what the problem could be?

---

### Post by Geekys on 2007-12-18
[http://www.gtk.org/download/](http://www.gtk.org/download/)

Try re-installing it. See if that'll work.

---

### Post by *daniel on 2007-12-27
I had the same error, and to get it working I installed this package from the repos:

```
libsdl1.2-dev
```

It compiled properly after that.

---

