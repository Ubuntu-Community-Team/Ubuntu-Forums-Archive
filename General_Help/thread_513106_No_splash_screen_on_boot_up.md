---
title: "No splash screen on boot up"
date: 2007-07-30
forum: General Help
---

### Post by dingley_del on 2007-07-30
Hello....I am a 2 day newbie to Ubuntu.  I have installed v7.04 successfully on my two computers and I am very impressed.  The forums have helped me sort out minor problems so far, except this one....

On the computer with a standard VGA monitor I see the whole boot up process.  My other computer has a Samsung Syncmaster 710mp and will not display the Ubuntu Progress screen (the bit between Grub and log-in screen).  The monitor goes black and displays ' mode unsupported'. The monitor will do this if it receives an unsupported resolution/refresh rate.  Once it gets to the log-in screen all is well.

I changed the menu.lst  file so that I can see the various Grub commands on screen.  It is after that the screen goes blank (until the log-in screen).

Is there any way I can alter the resolution/refresh rate for the Ubuntu progress splash screen?

changing the resolution/refresh rate System>Preferences makes no difference.

Don't make me go back to Windows!

Thanks for any help.

---

### Post by buixuanduong1983 on 2007-07-30
Can you press Alt+F1 during Ubuntu Progress screen? What you see there? I am not sure, but I think menu.lst will not help in this situation, it only change the menu of Grub.

---

### Post by dingley_del on 2007-07-30
Thanks for your reply.
I will try Alt+F1 later and let you know.  I realise the answer does not lie with menu.lst, but i'm hoping there is a config file somewhere that I can change.  I'm sure I came across something in one of the forums about screen res/horizontal and vertical sync rates etc. ..... I will go searching again.

---

### Post by dingley_del on 2007-07-30
Alt+F1 gives me text showing different systems/drivers being loaded......then into the login screen.

I will keep searching the forums, unless someone comes up with a possible solution.

---

### Post by dingley_del on 2007-07-30
I have just booted from the cd-rom.  At the menu screen I pressed F4(VGA) and selected 800x600 screen resolution. I see the Ubuntu progress screen!

Where is this setting in the normal system boot files?

Someone out there must know the solution.....don't force me back to Windows!

---

### Post by dingley_del on 2007-07-31
If anyone is interested I found the answer here....
[http://ubuntuforums.org/showthread.php?t=317888&highlight=no+splash+screen+while+booting]("http://ubuntuforums.org/showthread.php?t=317888&highlight=no+splash+screen+while+booting")

---

### Post by buixuanduong1983 on 2007-08-01
Sorry for late, because I was not at the office to read. So now you solved your problem, conratulation! Enjoy Ubuntu!

---

### Post by justinux on 2007-08-06
By the way Dingley, thanks for this thread, I was having the same problem with xubuntu on my laptop.

-Justin

---

### Post by strabes on 2007-08-07
Ha ha, that's exactly what I was going to tell you to do. I have seen the vga kernel boot options fix many things for many people.

---

### Post by staticvoid on 2007-11-04
mark this as solved folks :)

---

