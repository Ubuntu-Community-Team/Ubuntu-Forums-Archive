---
title: "[SOLVED] No Splash Screen on start up"
date: 2008-02-11
forum: General Help
---

### Post by cdsboy on 2008-02-11
Jeeze its been a while since i've been around here. So i just switched back to ubuntu after a fatal virus made me remeber why i hate xp. So anyways i just installed ubuntu on this laptop, and its running fine. Exept when i start it up after getting past the grub screen shows some white text for a second then stays blank for the remainder of the abnormally long (think like 1-2 minutes) boot time. Its not a huge deal, just annoying. So i was wondering if anyone has run into this before and knew how to help, or if anyone had any ideas.

---

### Post by y-lee on 2008-02-11
I'm not sure what is going on from your description. Is the white screen after grub and before login or after login in?

Check to see if usplash is installed if not install it

```
sudo apt-get install usplash
```

If it was installed try

```
sudo dpkg-reconfigure usplash
```

and

```
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by cdsboy on 2008-02-12
Thank you for the suggestions. I tried all of them and none of them worked. Does anyone else have any ideas?

---

### Post by apetresc on 2008-02-12
This issue may be non-solvable. Some video chipsets simply don't support the framebuffer.

When you're logged in normally, are you able to use Ctrl+Alt+F3 to go to a tty? If not, if all you get is a blank screen, then this is the problem and it's likely to be very difficult or impossible to fix.

I've resigned myself to this fate on my Macbook Pro. I got used to it pretty fast though, if that's any consolation...

---

### Post by y-lee on 2008-02-12
What version of Ubuntu are you using and what model laptop?

---

### Post by jalirious on 2008-02-12
Have you tried the alternative iso? It's easy to use, guided, etc. The result is the same as the usual iso.

---

### Post by cdsboy on 2008-02-12
i'm running gutsy, and i have an acer aspire 5050. Adrian i tried what you said and it brought me to a page with the terminal log in, however it was very streched. I'm not sure what was sposed to happen there. Also i just noticed that i have no sound. I have no idea of the two problems are related.

---

### Post by y-lee on 2008-02-12
> Also i just noticed that i have no sound. I have no idea of the two problems are related.

The sound issue is probably not hard to fix and i don't think it is related.

Try setting your sound preferences, from the thread [No sound on the Acer Aspire 5050]("http://ubuntuforums.org/newreply.php?do=newreply&p=3790630"):


> **joejoseph00 said:**
> Yes this works, I had to bump up the volume on SURROUND and enable SURROUND (even though there's only two speakers, it's because there's many inputs and outputs.  If you plug headphones into the headphone jacks your sound will work out of the box but to get the speakers working you have to turn on SURROUND and pump up the volume (using the sound adjustment in the System menu)  Modifying config files is not necessary.

I take it the machine does boot into Ubuntu tho and you can use it?

As to the no boot screen I saw some things yesterday we can try as I find it again and find time to get back on here.

---

### Post by y-lee on 2008-02-12
First we will try something simple. I found this on [answers.launchpad.net]("https://answers.launchpad.net/ubuntu/+question/19609")

> This is a change in Ubuntu 7.10 Gutsy Gibbon, done since the splash screen may slow down Gnome startup.

To enable the splash screen, do the following.
Press Alt-F2 and type **gconf-editor**.

Navigate to **/apps/gnome-session/options**.

Check the box next to the value **show_splash_screen**.

More information
This method uses the (Gnome) Configuration Editor. The Configuration Editor is hidden from the applications menu by default. To enable it in the applications menu, you can right-click the Applications menu, click Edit Menus and then you can see the lists of things in the Applications Menu (some may be disabled from appearing by default when they are unchecked, others you can uncheck if you don't want to see them). Click the System Tools menu (in the left-hand column) and then check Configuration Editor (in the right-hand column). There are many apps that you may not have heard about, so you can check the boxes and try out the apps.

As I said before, you may want to be careful with what you do in the Configuration Editor as it could damage your user interface if you do something silly.

---

### Post by chrisccoulson on 2008-02-12
> **cdsboy said:**
> Jeeze its been a while since i've been around here. So i just switched back to ubuntu after a fatal virus made me remeber why i hate xp. So anyways i just installed ubuntu on this laptop, and its running fine. Exept when i start it up after getting past the grub screen shows some white text for a second then stays blank for the remainder of the abnormally long (think like 1-2 minutes) boot time. Its not a huge deal, just annoying. So i was wondering if anyone has run into this before and knew how to help, or if anyone had any ideas.

You probably have a misconfigured resolution for usplash, which *is* fixable. This is a common problem on fresh Gutsy installs. To fix it, edit /etc/usplash.conf as root and set the xres and yres lines to the horizontal and vertical resolutions that your screen supports.

Then do
```
sudo update-usplash-theme usplash-theme-ubuntu 
```

---

### Post by cdsboy on 2008-02-12
Thank you chris! This is just what i've been looking for! it fixed my problem completely!

---

