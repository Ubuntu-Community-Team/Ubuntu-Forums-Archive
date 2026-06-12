---
title: "Dolphin Default Folder Links"
date: 2014-05-12
forum: General Help
---

### Post by Quarkrad on 2014-05-12
Can I change the default folder links in Dolphin?  E.g. Clicking on **Pictures** will take you to the **Pictures** folder in your **Home** directory  - I would like it to take me to a **Pictures** folder that is located somewhere else on my PC.  The same applies to Documents, Downloads, etc.

---

### Post by oldos2er on 2014-05-12
Do you mean the locations under "Places"? Right-click to edit.

---

### Post by Quarkrad on 2014-05-13
Yes - under Places, and I'm running 12.04.  Sorry, I need a bit further help - I've right clicked and tried various config options but I have not been able to change the location.  Any help appreciated.  (I would use nautilus but a family member who I'm trying to convert to Ubuntu has to have folder preview and I cannot get it to work - Dolphin provides folder preview (or thumbnails) easily).

---

### Post by speartip on 2014-05-13
Hi Quarkrad,
Yes its easy to do.
Go to System Settings / Account Details / Paths.
At the end of each line click on the folder icon & navigate to where your relevant folder is.
Click apply & you're sorted.

---

### Post by Quarkrad on 2014-05-13
Sorry to be bit stupid but where is System Settings?   The only one I know of is accessed via the far right icon in the top panel (where you go to log-off, shut down etc).  In this System Settings there is no Account Details / Paths in either 12.04 or 14.04.

---

### Post by speartip on 2014-05-13
What are you using?
I assumed you are using Kubuntu, because Dolphin is a KDE app!

---

### Post by Quarkrad on 2014-05-13
Sorry - I'm using Ubuntu 12.04 (and 14.04 but I really need to solve this for 12.04)

---

### Post by speartip on 2014-05-13
OK its unusual to be using Dolphin over Nautilus in Ubuntu.
In that case you need to install the kde system settings which controls dolphin.
```
sudo apt-get install systemsettings
```
Then follow the instructions in my last post.
This works for kubuntu, I cannot see why it won't work in Ubuntu, but I have never tried it, so it will be trial & error.

---

### Post by Quarkrad on 2014-05-13
I do not seem to have the Paths option under Account Details - perhaps this is because I'm using Ubuntu and not the 'normal' environment for Dolphin.  As you can see from the attached I only have **Social Desktop**. There seems to be nothing to do with Path anywhere.  Perhaps I need to start another thread to find if there is an 'easy' way to change Ubuntu's default paths.

---

### Post by speartip on 2014-05-13
Is there any reason why you are using Dolphin rather than the native Nautilus?
If you were using Nautilus the paths for user folders can easily be changed using a program called Ubuntu-Tweak.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by Quarkrad on 2014-05-13
I'm trying to convert a neighbour from win7 to ubuntu and a 'must have' is folder preview or thumbnails.  I just cannot get folder preview to work with nautilus whereas it is easy with Dolphin.

---

### Post by speartip on 2014-05-13
OK. But with what you are doing, maybe converting to Kubuntu would be better.
I have tried both flavours in 14.04, & Kubuntu for me is rock solid & a lot more flexible than Ubuntu.

---

### Post by SeijiSensei on 2014-05-13
Here's a solution that doesn't depend on which file manager you use:  create symbolic links in $HOME that point to the remote locations.  For instance, my /home/username/Documents directory is symlinked to a directory on my file server.

Try this:
```

cd ~
mv Pictures Pictures.old
ln -s /path/to/some/place/Pictures

```

Now /home/username/Pictures will point to /path/to/some/place/Pictures.  If there were pictures in the old directory that were not copied to that other location, you can copy them from /home/username/Pictures.old to /home/username/Pictures.

I'm a long-standing KDE user and would endorse switching to Kubuntu.  On weaker machines, I'll install Lubuntu or Xubuntu, but I always add some must-have KDE apps like Dolphin, Konsole, and Gwenview.

---

