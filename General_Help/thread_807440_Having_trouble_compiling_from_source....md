---
title: "Having trouble compiling from source..."
date: 2008-05-25
forum: General Help
---

### Post by soundprizm on 2008-05-25
Hello...  I'm having trouble with Jack-Rack.  The save and open dialog hang.  I know other people have this issue and have seemed to solve it by compiling from source.  I downloaded the latest version, extracted the .bz file, ran ./configure, but when I try to run 'make' I receive errors.  

These errors specifically:

	then mv -f ".deps/jack_rack-plugin_slot_callbacks.Tpo" ".deps/jack_rack-plugin_slot_callbacks.Po"; else rm -f ".deps/jack_rack-plugin_slot_callbacks.Tpo"; exit 1; fi
plugin_slot_callbacks.c: In function ‘slot_ablise_cb’:
plugin_slot_callbacks.c:112: error: ‘ui_t’ has no member named ‘midi_menu_item’
plugin_slot_callbacks.c:115: error: ‘ui_t’ has no member named ‘midi_menu_item’
plugin_slot_callbacks.c:118: error: ‘ui_t’ has no member named ‘midi_menu’
make[2]: *** [jack_rack-plugin_slot_callbacks.o] Error 1
make[2]: Leaving directory `/home/donnie/jack-rack-1.4.7/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/donnie/jack-rack-1.4.7/src'
make: *** [all-recursive] Error 1
donnie@soundprizm:~/jack-rack-1.4.7$ 


Am I doing something wrong or what?  I am still relatively new to linux so bare with me here! 

Any feedback is appreciated! Thanks!!

---

### Post by soundprizm on 2008-05-26
*bump*

---

### Post by EuPhobos on 2008-07-15
Becouse no ALSA support. Any way, compile from source, this no resolve the problem with open/save dialog hang.

---

### Post by cyclobs on 2008-07-15
> **soundprizm said:**
> Hello...  I'm having trouble with Jack-Rack.  The save and open dialog hang.  I know other people have this issue and have seemed to solve it by compiling from source.  I downloaded the latest version, extracted the .bz file, ran ./configure, but when I try to run 'make' I receive errors.  

These errors specifically:

	then mv -f ".deps/jack_rack-plugin_slot_callbacks.Tpo" ".deps/jack_rack-plugin_slot_callbacks.Po"; else rm -f ".deps/jack_rack-plugin_slot_callbacks.Tpo"; exit 1; fi
plugin_slot_callbacks.c: In function ‘slot_ablise_cb’:
plugin_slot_callbacks.c:112: error: ‘ui_t’ has no member named ‘midi_menu_item’
plugin_slot_callbacks.c:115: error: ‘ui_t’ has no member named ‘midi_menu_item’
plugin_slot_callbacks.c:118: error: ‘ui_t’ has no member named ‘midi_menu’
make[2]: *** [jack_rack-plugin_slot_callbacks.o] Error 1
make[2]: Leaving directory `/home/donnie/jack-rack-1.4.7/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/donnie/jack-rack-1.4.7/src'
make: *** [all-recursive] Error 1
donnie@soundprizm:~/jack-rack-1.4.7$ 


Am I doing something wrong or what?  I am still relatively new to linux so bare with me here! 

Any feedback is appreciated! Thanks!!

has something to do with the menu bar.

trying running make and see what comes up

---

### Post by cariboo on 2008-07-15
never mind.

---

