---
title: "Clam, nvidia, dvd, settings problems."
date: 2008-06-17
forum: General Help
---

### Post by Milardo on 2008-06-17
Hi, I am having several issues which need immediate attention. I have onboard sound Realtek alc888. I've got a problem when it comes to hearing sounds for the computer startup, logoff, etc. I changed it in the properties of that but it doesn't seem to work or play the sound, rather it plays the default sound. Also the sound for just one game, Wolfenstein Enemy Territory has never worked. I don't know what to do about it I changed the sound device many times. Should I try and install realtek linux version driver?

Next for the graphics card. Its a nvidia card. My problem is that although I change the settings through x server settings, when I restart the computer and get back in the sound settings go back to default! How can I change this? 

Clam antivirus says I have to be root to update the definitions? Does that mean I have to login as root just to update definitions?

In terminal, when you have to enter cd to move to folders, it won't let me move to folders that have spaces, do I have to enter something to fix this like a special character?

In the login screen I heavily changed how it looks, however it won't let me keep gnome interface each time it gets to login screen. It keeps going to default.

Can anyone recommend a good dvd/vcd/svcd program that works with menus/ chapters, etc besides mplayer, ogle?

How about a good tv tuner /video capture program?

Lastly I tried to download this program.

[http://www.cyberlink.com/english/products/powercinema/pcm-linux/pcmlinuxgpl.jsp](http://www.cyberlink.com/english/products/powercinema/pcm-linux/pcmlinuxgpl.jsp)

Is there someway to compile and make it work?

I feel I should have to login as root as it seems easier to do anything.

Thanks in advance for any answers anyone might have.

---

### Post by cariboo on 2008-06-18
> Hi, I am having several issues which need immediate attention. I have onboard sound Realtek alc888. I've got a problem when it comes to hearing sounds for the computer startup, logoff, etc. I changed it in the properties of that but it doesn't seem to work or play the sound, rather it plays the default sound. Also the sound for just one game, Wolfenstein Enemy Territory has never worked. I don't know what to do about it I changed the sound device many times. Should I try and install realtek linux version driver?

If your sound is working on login that you have the correct driver.

> Clam antivirus says I have to be root to update the definitions? Does that mean I have to login as root just to update definitions?

Unless your are forwarding a lot of windows mail you don't need anti virus software.

> In terminal, when you have to enter cd to move to folders, it won't let me move to folders that have spaces, do I have to enter something to fix this like a special character?

Encapsulate the file name with spaces in quote marks like this

```
sudo mv "file with space"
```

> In the login screen I heavily changed how it looks, however it won't let me keep gnome interface each time it gets to login screen. It keeps going to default.


Gonme-desktop is the default

> Can anyone recommend a good dvd/vcd/svcd program that works with menus/ chapters, etc besides mplayer, ogle?

Mplayer does menus and chapters click on Go

> How about a good tv tuner /video capture program?

What make/model of tv tuner card do you have?

> Lastly I tried to download this program.

[http://www.cyberlink.com/english/pro...cmlinuxgpl.jsp](http://www.cyberlink.com/english/pro...cmlinuxgpl.jsp)

Is there someway to compile and make it work?

Unzip it and check the readme file it will tell you what you need and how to do it.

> I feel I should have to login as root as it seems easier to do anythin

That is what sudo is for.

Jim

---

### Post by Milardo on 2008-06-18
Thanks for your reply.

---

