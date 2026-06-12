---
title: "Wesnoth installing problems"
date: 2006-11-11
forum: General Help
---

### Post by jpe2000 on 2006-11-11
Okay, I'm running Ubuntu 6.1.

I am having a problem with the make in Wesnoth. Here's the error.

```
depbase=`echo clipboard.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`; \
        if g++ -DHAVE_CONFIG_H -I. -I/home/josh/Desktop/wesnoth-1.1.11/src -I..   -I/usr/include/freetype2 -I /home/josh/Desktop/wesnoth-1.1.11/src/sdl_ttf -I../intl -I/home/josh/Desktop/wesnoth-1.1.11/intl -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\"  -O2 -W -Wall -ansi  -D_X11    -MT clipboard.o -MD -MP -MF "$depbase.Tpo" -c -o clipboard.o /home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp; \
        then mv -f "$depbase.Tpo" "$depbase.Po"; else rm -f "$depbase.Tpo"; exit 1; fi
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In member function ‘Display* XHelper::dpy()’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:103: error: ‘struct SDL_SysWMinfo’ has no member named ‘info’
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In member function ‘Window XHelper::window()’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:108: error: ‘struct SDL_SysWMinfo’ has no member named ‘info’
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In member function ‘void XHelper::acquire()’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:118: error: ‘struct SDL_SysWMinfo’ has no member named ‘info’
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In member function ‘void XHelper::release()’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:126: error: ‘struct SDL_SysWMinfo’ has no member named ‘info’
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In function ‘void handle_system_event(const SDL_Event&)’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:178: error: ‘struct SDL_SysWMmsg’ has no member named ‘event’
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:185: error: ‘XA_PRIMARY’ was not declared in this scope
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:211: error: ‘XA_ATOM’ was not declared in this scope
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In function ‘void copy_ucs2_to_clipboard(const ucs2_string&)’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:248: error: ‘XA_PRIMARY’ was not declared in this scope
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In function ‘void copy_to_clipboard(const std::string&)’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:262: error: ‘XA_PRIMARY’ was not declared in this scope
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In function ‘ucs2_string copy_ucs2_from_clipboard()’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:340: error: ‘XA_STRING’ was not declared in this scope
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp: In function ‘std::string copy_from_clipboard()’:
/home/josh/Desktop/wesnoth-1.1.11/src/clipboard.cpp:363: error: ‘XA_STRING’ was not declared in this scope
make[2]: *** [clipboard.o] Error 1
make[2]: Leaving directory `/usr/Games/Wesnoth/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/Games/Wesnoth'
make: *** [all] Error 2

```


What's wrong. I have all the required libraries and the SDL stuff. Thanks.

---

### Post by giants_fan on 2006-11-11
You can just install via the "Add/Remove Applications" app (Applications->Add/Remove->Games).

I installed it last week that way and it works fine.

---

### Post by jpe2000 on 2006-11-11
I know that. I just want the most updated. And plus installing that way is boring for me. I like installing from source.

---

### Post by jpe2000 on 2006-11-12
bumps

---

### Post by jpe2000 on 2006-11-12
c'mon...please help me

---

### Post by David Corrales on 2006-11-12
I just installed it a few days ago on this Edgy box with no problems. Did you install all the -dev packages, not just the regular ones?

---

### Post by jpe2000 on 2006-11-12
Yes I did but at first it didn't "see" that I did until I had moved the .so files or whatever they are called and I had to move them to a different place (that was for SDL though). Anyway, I don't see anything else really that's wrong with it. Also, when I try to click the adjust button when I right click on the time, Bugzilla keeps poping up and I can never change the time. Please help me with this too. Thanks.

---

### Post by jpe2000 on 2006-11-13
...

---

### Post by jpe2000 on 2006-11-13
again...bump

---

### Post by nova- on 2006-11-23
@jpe: Hi,

I had a similar-ish problem recently, which I fixed.
this might help you: [http://homesource.nekomimicon.net/sourceforum/viewtopic.php?t=129](http://homesource.nekomimicon.net/sourceforum/viewtopic.php?t=129) 

good luck,
nova

---

### Post by jpe2000 on 2006-11-26
Same damn error...could it be Ubuntu itself that is causing the problem?

---

### Post by nova- on 2006-11-27
jpe,

someone else, but on debian, is having the same or similar problem:
[http://www.wesnoth.org/forum/viewtopic.php?p=186620&sid=dda08367c58a8802e46885a683c65378](http://www.wesnoth.org/forum/viewtopic.php?p=186620&sid=dda08367c58a8802e46885a683c65378)


i'd suggest posting in there, or starting a new thread over there

---

