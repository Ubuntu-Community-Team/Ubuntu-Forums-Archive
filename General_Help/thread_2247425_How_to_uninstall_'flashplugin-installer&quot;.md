---
title: "How to uninstall 'flashplugin-installer&quot;"
date: 2014-10-07
forum: General Help
---

### Post by sillyboy on 2014-10-07
Hello all,

What is the correct way in the terminal to totally purge "flashplugin-installer", or any other program?

Thank You

---

### Post by Dennis N on 2014-10-07
```
sudo apt-get purge flashplugin-installer
```

> purge is identical to remove except that packages are removed and purged (any configuration files are deleted too)
---from man page for apt-get

---

### Post by sillyboy on 2014-10-07
Thanks Dennis N

Ubuntu 12.04, Gnome 2...

I did that and Shockwave Flash 15.0.0.152 is still in my plugins.  That command took out my Shockwave Flash 11.2.202.404.  I just wanted to get rid of SWF 15.xxx. SWF 15.xxx is the one causing all my problems.

What should I do? 

Thanks again

---

### Post by Dennis N on 2014-10-07
The flash plugin used by Firefox is installed by flashplugin-installer. My current version of that is 11.2.202.406. If you want it back, just install flashplugin-installer again. What 15.0.0.152 is I am not sure but it could be the pepperflashplugin-nonfree used by chrome and chromium browsers. Sorry, but I don't have either one of those to check.

---

### Post by sillyboy on 2014-10-08
Thanks,

I need to uninstall SWF 15.x and reinstall SWF 11.x.  SWF 15.x when enabled semi crashes (?) my computer constantly and I get nowhere fast. When SWF 15.x is off everything is wonderful...well, almost wonderful. ):P   SWF 11.x is a must have for U 12.04   If a video is not supported by HTML 5, I can't watch it.

Thanks

---

### Post by sillyboy on 2014-10-09
Thanks,

    I need to uninstall (purge) SWF 15.x (in Plugins) and reinstall SWF 11.x. SWF 15.x when enabled semi crashes (?) my computer constantly and I get nowhere fast. When SWF
    15.x  is off  everything is wonderful...well, almost wonderful. SWF 11.x is a must have for U 12.04 If a video is not supported by HTML 5, I can't watch it.

    Thanks again for your help  :p

---

### Post by vasa1 on 2014-10-09
You already have a very related thread here: [http://ubuntuforums.org/showthread.php?t=2247425](http://ubuntuforums.org/showthread.php?t=2247425)

---

### Post by slickymaster on 2014-10-09
Threads merged.

Please do not create duplicate threads, it dilutes community effort.

---

### Post by vasa1 on 2014-10-09
> **sillyboy said:**
> Thanks Dennis N

Ubuntu 12.04, Gnome 2...

**I did that and Shockwave Flash 15.0.0.152 is still in my plugins.**  That command took out my Shockwave Flash 11.2.202.404.  I just wanted to get rid of SWF 15.xxx. SWF 15.xxx is the one causing all my problems.

**What should I do? **

Thanks again
What you can do is
[LIST]
[*]put up a snapshot of your plugins page
[*]tell us exactly which browser you're using; note that Google Chrome !== Chromium
[/LIST]

Without such information people have to guess.

---

### Post by sillyboy on 2014-10-09
Is anyone really reading my posts???  I posted a new thread because I am not receiving any answers lately...  Going to Adobe for help = 0.  

How do I purge Shockwave Flash 15.0.0.152 from my Plugins.  Uninstalling  'flashplugin-installer" does not uninstall Shockwave Flash 15.0.0.152.  It just uninstalled Shockwave Flash 11.2.202.406, the one I needed.  

Thanks for the help so far.

---

### Post by vasa1 on 2014-10-09
> **sillyboy said:**
> Is anyone really reading my posts???  I posted a new thread because I am not receiving any answers lately... .
You should try to provide more information :)

---

### Post by coffeecat on 2014-10-09
> **sillyboy said:**
> Is anyone really reading my posts???

Did you read the replies, asking you about pepperflash? Pepperflash in Chromium/Chrome shows up as "Adobe Flash player 15.0.0.152". What browser are you using? have you installed the package pepperflashplugin-nonfree?


> **sillyboy said:**
> I posted a new thread because I am not receiving any answers lately

Cross posting is as much against the rules here as on all other forums that I have ever been on. You were receiving relevant replies.

---

### Post by sillyboy on 2014-10-10
Is anyone out there?????  Help!!!

---

### Post by sammiev on 2014-10-10
> **sillyboy said:**
> Is anyone out there?????  Help!!!

People are asking you questions and to post a picture of your plug-ins and so on. If you really want help read back and start answering the questions.

---

### Post by vasa1 on 2014-10-10
> **sammiev said:**
> People are asking you questions and to post a picture of your plug-ins and so on. If you really want help read back and start answering the questions.
Maybe the OP's account is being accessed by someone else who's just having some "fun"?

---

### Post by sammiev on 2014-10-10
> **vasa1 said:**
> Maybe the OP's account is being accessed by someone else who's just having some "fun"?

LOL, but really a few answers would be helpful.

---

### Post by sillyboy on 2014-10-12
Thank You

---

### Post by Mike_Walsh on 2014-10-12
Hi.

In all honesty, if you won't help yourself by providing a wee bit more information for us to look at, I don't see how the members of these forums CAN help you. Even experienced users, of many years standing, need SOMETHING to go on... We can't conjure answers  up out of thin air, off the top of our heads, you know.

It would be VERY helpful to know 

1) What browser you are using, and
2) Whether you installed pepperflashplugin-nonfree (since it can ONLY be this, as Firefox only uses version 11.2 of the Shockwave Flash Player).

It WOULD help.

Regards,

Mike.

---

