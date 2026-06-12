---
title: "Annoying beep on shutdown"
date: 2008-05-05
forum: General Help
---

### Post by snova on 2008-05-05
When I shut down my laptop, it beeps. This is to be expected from a terminal, but Debian (which I used previous to Ubuntu) never beeped when I shut it down from KDE.

How do I make it stop? Can I? Or is the solution really obvious?

I expect this is because of the way I have it set up. I installed the minimal command line system from the disks and put X and KDE on manually. I never installed KDM. As a result, it boots to a login: prompt, which I don't mind. I type [FONT="Courier New"]'startx; logout[/FONT]' as soon as the shell starts up.

To actually shut it down, I run '[FONT="Courier New"]sudo halt[/FONT]' from a Konsole.

Considering all these quirks of my installation, it's probably something I did. But it doesn't explain why it only beeps some of the time. Sometimes it remains silent.

I'm using Ubuntu version 7.10.

The subject prefix [FONT="Courier New"][kubuntu][/FONT] may be inappropriate. I didn't buy a special variant of Ubuntu. I just installed different packages then the installer would have, because I assumed I would get the same thing.

---

### Post by retrow on 2008-05-05
Under Sound preferences, disable system beep.

---

### Post by eriqjaffe on 2008-05-05
If you prefer a command-line method, in a terminal, you can type

```
sudo gedit /etc/modprobe.d/blacklist
```

and add

```
blacklist pcspkr
```

to the end of the file.  When you reboot, the speaker will be mercifully silent.

---

### Post by snova on 2008-05-05
It worked. Thank you.

---

### Post by |UVI| on 2009-01-09
I got same beep during system startup.
I've tryed previous commands without success :(

Anyone could help me?

---

### Post by HunterK on 2009-01-09
> **|UVI| said:**
> I got same beep during system startup.
I've tryed previous commands without success :(

Anyone could help me?

You sure that's not your computers POST signal? (Power on self test)  Your computer will beep when everything checks out ok right when you turn it on.  In other words, it may not be an Ubuntu thing.

---

### Post by |UVI| on 2009-01-09
I've just solved turning down volume of beep on  using alsamixer command


kind regards

---

### Post by jiggz88 on 2009-01-15
I've got something a bit more interesting than one that just beeps on shutdown. It seems if I try to backspace anywhere that I cant or there is nothing more to 'backspace', I get nailed with a nasty system beep for every X time I hold the backspace. Now when I disable alerts in sound, it seems to turn it off but I want to know why some of the alerts came through the speakers and some as a system beep.

EDIT: further more, when doing a lspci |grep audio, i get nothing, which is telling me the reason why its doing it all as system beeps is due to it probably not fully recognizing the audio chipset. The funny thing is that alsa, oss, and pulseaudio all work fine for sending audio through the speakers and headphones.

---

### Post by mr.wireful10000 on 2009-03-02
Thanks for the solution, that beep was getting bothersome...

---

### Post by endref on 2009-06-14
I am running Ubuntu 9.04 and I also get the system beep on logout.

But when I check the settings for sound I see there is supposed to be a nice logout sound. I dont get this one, but only the beep. Could there be something wrong with the setup of my sounds? The login sound works.

I don't want to just disable all system beeps, because this could be useful if an error does occur.

Have anyone found a solution for getting the logout sound instead of the beep?


Endre

---

### Post by kaboyish on 2009-10-11
> **eriqjaffe said:**
> If you prefer a command-line method, in a terminal, you can type

```
sudo gedit /etc/modprobe.d/blacklist
```

and add

```
blacklist pcspkr
```

to the end of the file.  When you reboot, the speaker will be mercifully silent.

thanks man. this has really helped. just wanted to ask you whether you know any guides that'll teach me how to use the terminal. i'm a newbie

---

### Post by alexxroche on 2009-12-08
# This worked for me with 9.04

echo "*** gdm.arch    2009-12-08 09:10:33.000000000 +0100
--- gdm    2009-12-08 09:15:42.000000000 +0100
*************** case \"$1\" in
*** 89,94 ****
--- 89,95 ----
    ;;
    stop)
      log_begin_msg \"Stopping GNOME Display Manager...\"
+     rmmod $(lsmod|grep pcsp|awk '{print $1}'); #stop system spkr beep
      start-stop-daemon --stop  --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG --retry 30 >/dev/null 2>&1
      log_end_msg 0
    ;;
" >> /tmp/patch_gdm 
patch /etc/init.d/gdm !$ && echo "Gnome has been patched to STFU on shutdown"; 
rm /tmp/patch_gdm # clean up after (though a reboot would do this as well)

# This is a patch file and then the command to apply it. It probably does not work for [k|x]ubuntu 
# It depends on rmmod, lsmod, grep, awk: if any are missing from your system this will error

---

