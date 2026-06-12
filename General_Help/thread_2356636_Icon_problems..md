---
title: "Icon problems."
date: 2017-03-25
forum: General Help
---

### Post by Furycd001 on 2017-03-25
Hey Guys.

Yesterday I let a friend borrow my laptop. I've booted it up this morning to find that my icons are somehow completely messed up. None of my icons, be it gnome, gnome-colors, dropline nuovo, adwaita or standard humanity-icons work as expected. If you look at the screenshot below you can see that plenty of icons are missing from my panel & you can also see that whenever I go to click on something the mouse pointer reverts to something really old and ugly looking. Could someone please tell me how I can sort out my icons so that they show correctly without any appearing as missing, I have already tried re-installing / uninstalling & re-installing each icon set via synaptic. Thank you very much for your time and help...

[http://i.imgur.com/nHm1XBF.png](http://i.imgur.com/nHm1XBF.png)

---

### Post by vasa1 on 2017-03-25
From #4 in the [Forum's Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"):> If you include screenshots, use the forum attachment system rather than an offsite host such as imgur.To do so, click on the paper clip icon *above* the area in which you are composing your post. If you don't see the paper clip icon, click on "Go Advanced" *below* the area in which you are composing your post.

---

### Post by ajgreeny on 2017-03-25
I hope you did not allow your friend to login to and use your own user account?

Not a good idea at all and is a huge security risk. This is precisely what the Guest user account is for.
If he was using your own user account I can only assume that your friend has somehow changed your desktop settings.

If you have a complete backup of all of your home folders and files you can simply replace the current ~/.config/xfce4 and xfce4-session folders by renaming them and restoring the backups; hopefully you should then be back where you were before.

However, what else might have happened if he was logged in as you is impossible for us to say.

---

### Post by Furycd001 on 2017-03-25
Thank you very much for your replies. I know now to use the attachment from now on :-) My friend did only have access to a guest account, but they also had access to a bootable mint usb. They say they done nothing other than open up their presentation, but it's fair to say that something more has went on.

---

### Post by ajgreeny on 2017-03-25
> **jonny6 said:**
> Thank you very much for your replies. I know now to use the attachment from now on :-) My friend did only have access to a guest account, [COLOR="#FF0000"]but they also had access to a bootable mint usb.[/COLOR] They say they done nothing other than open up their presentation, but it's fair to say that something more has went on.
Oh dear!
That would immediately give them full access to anything on your OS unless your home was encrypted.

Do you have any backups as I queried in my last post?

---

