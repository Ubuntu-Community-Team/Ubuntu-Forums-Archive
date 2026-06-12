---
title: "Ubuntu 16.04 Black screen on boot, grub not enabling networking, and more"
date: 2018-02-20
forum: General Help
---

### Post by baulderan on 2018-02-20
Hey everyone. I'm going to preface this post with saying that I am extremely new to linux systems and may need more step-by-step instructions than normal. I appreciate your patience!

**A Short Summary of What's Known**
- The computer boots to a black screen. Sometimes a purple screen
- Grub will not enable networking, giving me errors about a user "geoclue" in the message bus. This happens even after I did an uninstall of geoclue (and then lost my GUI. Oops.)
- If I go into grub and tell it to continue to boot normally I now get into the TTY. From here I can ping my entire internal network, but not an external network (i.e. 8.8.8.8). I can ping my router.
- Just turning it on and not going through grub gives me a black screen again
- Plex will work even in this weird black screen state
- I did follow the LiveCD recovery guide from Ubuntu. Or, tried to. I was told that I had three partitions-- sda1, 2, and 3. When I tried to mount 1 or 2, it said it had no mount point. Sda3 said it didn't know how to mount LVM2_Member.

I have no idea what caused any of this. It was trucking along just fine right up until a week ago. I noticed it when I suddenly couldn't VNC into it. I pulled it out and plugged it into my TV and was greeted with a black screen. I tried googling error messages and following instructions, but I feel as lost as ever. I'm not even sure where to go from here, it's all dead ends. Any help would be enormously appreciated.

---

### Post by tinylagarto on 2018-02-20
You say it worked perfectly before. Can you remember if there was a kernel update? 

Which kernel are you using?

You can post the output of this command:

```
uname -r

```
when you are in tty.

---

### Post by baulderan on 2018-02-20
I can't imagine I would have updated my kernel manually. Is it possible ubuntu would do that sort of thing automatically? That's not exactly the sort of thing I'd do haha

Kernel is 4.13.0-32-generic.

---

### Post by tinylagarto on 2018-02-21
I guess the kernel updates in the background as a security update with unattended upgrades enabled. 

Do you have older kernels on this machine and could boot into an older one? Just to see if the problem persists. 

Reboot the machine and press the shift key. You should see the Grub menu. Select an older kernel entry.

I am probably shooting in the dark but I would try it.

---

### Post by baulderan on 2018-02-21
Honestly, I just spent last night throwing random things at it and got it into a functional state, although not everything is working super (still can't enable networking in grub). Turns out I couldn't access the internet in tty because my router of all thing was messing up and was confused about the NAT. I got that working and now it can access the internet.

I attempted briefly to get a UI back by running ```
sudo apt-get --reinstall ubuntu-desktop
``` but my god that broke everything-- no GUI and suddenly I couldn't type into my tty! Ended up needing to do a purge of xserver before it worked.

Looks like this is now Ubuntu Server and I get to do everything via terminal. Well, it'll certainly make me learn it...

---

