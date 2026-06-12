---
title: "No sound in ubuntu"
date: 2007-04-20
forum: General Help
---

### Post by carlosqueso on 2007-04-20
I've had this problem for a while, but since I'm having trouble compiling my kernel, I figured I'd ask about it.  I have an old computer with integrated sound.  lspci lists it as ```
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06) 
``` and ALSA seems to recognize it, but no sound.  However, if I compile ALSA and the ESS1371 driver directly into the kernel, it works fine.  Why is this, and is there a way to get the same result without recompiling my whole kernel every time there's an update?

Thanks for the help

---

### Post by ashz on 2007-04-20
I had a problem like this for ages on one of my old boxes, me being the idiot that i am had not checked the volume control, turns up the volume was not up... doh

I know it does not help u much soz...

Hope u find a solution
Ash

---

### Post by carlosqueso on 2007-04-20
played with the volume, doesn't help.   Like I said, I do have a work around, but I'm sure there's an easier solution that I just lack to knowledge to implement.

---

### Post by Loki-uk on 2007-04-20
Read the Sound setion on this site it refers to an SB16 soundcard but at the end of the article it tells you what you need to use for difeerent sound cards.

[www.aotk50.dsl.pipex.com/default.htm](www.aotk50.dsl.pipex.com/default.htm)

hope this helps

Brian

---

### Post by carlosqueso on 2007-04-25
An update:

I tried the suggestions in that post, but the proper modules for my soundcard (ESS 1371/1373) were already installed and running....I could also control the volume of the static by raising or lowering the volume through alsamixer or the xfce control panel.   

I also tried my previous workaround by compiling ALSA and my soundcard driver directly into the kernel.  That gave the same symptoms.

I did get my card to work using the OSS drivers, but they aren't as good.  

Is this a bug with ALSA? Is there something else I can do?  I've posted the relevant lspci -v data about my card (don't laugh at my old hardware), let me know if anyone has ideas...

```
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
        Subsystem: Micron Tazer
        Flags: bus master, slow devsel, latency 32, IRQ 5
        I/O ports at d800 [size=64]
        Capabilities: [dc] Power Management version 1

```

---

### Post by carlosqueso on 2007-05-11
bump

---

### Post by sglow on 2007-05-11
I have the same problem with essentially the same card.  No sound no matter how much I fool with the thing.

My card, according to lspci -v is:

00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
        Subsystem: Micron Tazer
        Flags: bus master, slow devsel, latency 32, IRQ 5
        I/O ports at d800 [size=64]
        Capabilities: [dc] Power Management version 1


I haven't tried compiling it directly into the kernel yet.  I'll have to give that a try.

This is with 7.04.  If I boot from the 6.10 install CD the sound works fine.

Steve

---

### Post by Eddi3 on 2007-05-12
I've also had the same problem for a while now. lspci -v gives me:
[INDENT]
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
        Subsystem: Micron Tazer
        Flags: bus master, slow devsel, latency 32, IRQ 12
        I/O ports at e800 [size=64]
        Capabilities: [dc] Power Management version 1[/INDENT]

It looks like we all have the same problem with similar Micron boxes. I've messed with the Mixer endlessly, to no avail. The sound worked in 6.10.

How would I go about compiling ALSA and the correct driver directly into the kernel?

Thanks,

 - Eddie

---

### Post by tommcd on 2007-05-12
Have you seen this:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
This is a systematic way to troubleshoot any sound problem.

---

### Post by Eddi3 on 2007-05-13
Yes, I have. Thanks, though.

---

### Post by yotam on 2007-05-14
The tip  in [http://www.ubuntux.org/no-sound-on-ubuntu-dapper#comment-349](http://www.ubuntux.org/no-sound-on-ubuntu-dapper#comment-349)
helped me solve the problem. But what I actually  *did* was:[LIST]
[*]Install **gnome-alsamixer**
[*]Run [FONT=Courier New]gnome-alsamixer[/FONT] and there
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32560&stc=1&d=1179124678[/IMG]
        *uncheck* the 
   **Jack Detect** item.[/LIST]

---

### Post by Eddi3 on 2007-05-14
Thanks for your input.

I installed gnome-alsamixer, ran it, and a curious error popped up:

```

Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Master": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Master": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Master_Mono": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Master_Mono": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Center": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Center": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Depth": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Depth": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-PCM": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-PCM": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Line": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Line": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-CD": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-CD": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mic": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mic": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Video": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Video": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Phone": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Phone": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-PC_Speaker": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-PC_Speaker": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Aux": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Aux": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Capture": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Capture": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Switch": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-3D_Control_-_Switch": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-PCM_Out_Path___Mute": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-PCM_Out_Path___Mute": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mic_Boost___20dB_": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mic_Boost___20dB_": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mic_Select": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mic_Select": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mono_Output_Select": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mono_Output_Select": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mix": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mix": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mix_Mono": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Mix_Mono": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Caller_ID": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Caller_ID": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Off-hook": '?' is not an ASCII character, so isn't allowed in key names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/0x43004e53_C&#65533;N,0x43004e53_C&#65533;N-Off-hook": '?' is not an ASCII character, so isn't allowed in key names

```

This makes me think that *maybe* the way Feisty assigns names to devices is screwing things up.

Also, there was no item called "Jack Detect" to uncheck. There was, however, a plethora of other options which I've tried toggling with, to no avail.

It may be a matter of just changing the name of the onboard sound card.

Thanks for the help,

Eddie

---

### Post by Eddi3 on 2007-05-15
Another note:

After using gnome-alsamixer, I no longer hear static in my speakers (when I turn up my volume all the way), whereas I did before.

Anyway, would anybody care to link me to some other sound drivers?

EDIT: Rather, would anybody care to let me know how to switch to the OSS drivers instead of ALSA?

---

### Post by ghink on 2007-05-16
Please post your solution to your sound issue whether it is finding out how to make it work with ALSA or how you made OSS work. It sounds like we have the same PC (Mircon using Tazer motherboard and onboard Ensonig 1373 audio. Actually it is a Tyan Trinity 400 motherboard if you have the same computer as me.). I have had the exact same issue even down to the static if you crank the volume of the speakers. 

Thanks,
Gregg

---

### Post by carlosqueso on 2007-05-16
What I did is went into my kernel config (use [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild) and scroll to Old Debian way for the way to do it), and took out ALSA completely, then compiled OSS and the ES1371 drivers directly into the kernel.  Sound drivers are under Device Drivers -> Sound.  I may go home and try yotam's solution though.

---

### Post by Eddi3 on 2007-05-16
I just did a fresh install of Xubuntu Feisty before I started.

First, I ran the following:

sudo apt-get install linux-kernel-devel fakeroot kernel-wedge kernel-package
sudo apt-get build-dep linux-source

Now, when I type 'make menuconfig' I get the following errors:

```
eddie@ServerBox:~/src/linux-source-2.6.20$ make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before &#8216;chtype&#8217;
scripts/kconfig/lxdialog/dialog.h:187: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:193: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:195: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:196: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:197: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:198: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:200: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:31: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:59: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:95: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c: In function &#8216;dialog_checklist&#8217;:
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;WINDOW&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;dialog&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;list&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function &#8216;getmaxy&#8217;
scripts/kconfig/lxdialog/checklist.c:129: error: &#8216;stdscr&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: &#8216;KEY_MAX&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function &#8216;getmaxx&#8217;
scripts/kconfig/lxdialog/checklist.c:137: error: &#8216;COLS&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: &#8216;LINES&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function &#8216;draw_shadow&#8217;
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function &#8216;newwin&#8217;
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function &#8216;keypad&#8217;
scripts/kconfig/lxdialog/checklist.c:143: error: &#8216;TRUE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function &#8216;draw_box&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function &#8216;wattrset&#8217;
scripts/kconfig/lxdialog/checklist.c:147: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function &#8216;mvwaddch&#8217;
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function &#8216;waddch&#8217;
scripts/kconfig/lxdialog/checklist.c:151: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function &#8216;print_title&#8217;
scripts/kconfig/lxdialog/checklist.c:156: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function &#8216;print_autowrap&#8217;
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function &#8216;subwin&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function &#8216;print_item&#8217;
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function &#8216;print_arrows&#8217;
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function &#8216;print_buttons&#8217;
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function &#8216;wnoutrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function &#8216;doupdate&#8217;
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function &#8216;wgetch&#8217;
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_UP&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_DOWN&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: &#8216;FALSE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function &#8216;scrollok&#8217;
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function &#8216;wscrl&#8217;
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function &#8216;wrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function &#8216;delwin&#8217;
scripts/kconfig/lxdialog/checklist.c:297: error: &#8216;KEY_LEFT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: &#8216;KEY_RIGHT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function &#8216;on_key_esc&#8217;
scripts/kconfig/lxdialog/checklist.c:312: error: &#8216;KEY_RESIZE&#8217; undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2

```

Also, how would I go about taking out the ALSA drivers, and compiling the correct driver right into the kernel?

---

### Post by carlosqueso on 2007-05-17
You need to install libncurses5-dev and probably build-essential.  Once you get the menu up, just go to Device Drivers -> Sound and you should be able to answer no to alsa (press N) and yes to OSS.  I just want to say that this is not a first choice fix (it's a pain, takes a while and leaves you with an inferior driver), but it seems to be the only way to get sound.

---

### Post by Eddi3 on 2007-05-17
libncurses5-dev and build-essential were both already up to date. 

I'm currently ssh'd into my home computer from school, and I'm going to try to get it to work again.

VERY weird. It seems to have worked, even though I've not changed anything since yesterday... Now to compile the kernel. I'll report back, but anyway...

Have you tried installing more recent ALSA drivers? I'm not at home, but I think the currently used version in Feisty is 1.0.11, while the current stable release is 1.0.13, and 1.0.14rc4 is out. I thought that might be worth a try. If you havn't tried that, I might give it a go...

Also, I understand that this isn't the first option, but if you have a better one, let me know ;-)

---

### Post by carlosqueso on 2007-05-17
I had tried on gentoo before, but not on Ubuntu...let me know if you have success with those.  Maybe between the two of us we can get ALSA working with our old computers

---

### Post by Eddi3 on 2007-05-17
Alright, I've got it all config'd. I set the ES1371 driver to be compiled directly into the kernel, and the rest as modules (just incase...?). I'll start the process when I get home.

EDIT: Alright, it's 3:30, And I'm starting the compile.

EDIT2: Well, it's 12:17 am and I'm done. It really wouldn't have taken that long, but I had no idea how much disk space this operation required.

I now have 2 debs; one that's ~207 MB, and one that's ~8 MB. I'm gonna run them and hope for sound after a restart.

EDIT3: Well, sound is working, but wireless internet isn't. I don't know, really, how to go about compiling the restricted modules...

---

### Post by Eddi3 on 2007-05-20
Alright. So, after a few days, I finally got around to making this work.

After I recompiled the kernel, the sound was working, however, this removed access to the Restricted Drivers Manager, and the Drivers it applies to the system. I tried to use a HowTo to symlink, by kilou here: [http://ubuntuforums.org/showthread.php?t=441013](http://ubuntuforums.org/showthread.php?t=441013)

That basically worked, but I ended up reinsalling the madwifi drivers manually, but the Restricted Drivers Manager is now working, AND I HAVE SOUND!!!

In addition, I also made a lot of tweaks, removing a lot of things I didn't need from the kernel, and my computer is much faster for it.

Eddie

---

### Post by carlosqueso on 2007-05-21
That's the disadvantage to a custom kernel, but I'm glad it worked.

---

### Post by 8-Ball on 2007-06-20
> **yotam said:**
> The tip  in [http://www.ubuntux.org/no-sound-on-ubuntu-dapper#comment-349](http://www.ubuntux.org/no-sound-on-ubuntu-dapper#comment-349)
helped me solve the problem. But what I actually  *did* was:[LIST]
[*]Install **gnome-alsamixer**
[*]Run [FONT=Courier New]gnome-alsamixer[/FONT] and there
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32560&stc=1&d=1179124678[/IMG]
        *uncheck* the 
   **Jack Detect** item.[/LIST]
This worked!
It was muted all this time :P I feal a but stupid now but that you very much. I solved all my (ubuntu related) problems :D thank you!

---

