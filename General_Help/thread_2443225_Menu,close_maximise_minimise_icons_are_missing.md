---
title: "Menu,close maximise minimise icons are missing"
date: 2020-05-12
forum: General Help
---

### Post by shankar-pudi3 on 2020-05-12
[FONT=comic sans ms]I have recently upgraded to 20.04 But After Reboot The Menu Icons 
I have Recorded A videoso  that you can clearly get the problem
I think there is problem in the gnome shell
what are your thoughts ?
pls help
thanks in advance

[https://drive.google.com/open?id=1kBYY_0sBIAlT-WFLkNtrJaygtMPHIc_8](https://drive.google.com/open?id=1kBYY_0sBIAlT-WFLkNtrJaygtMPHIc_8)

the icons and names in the below attachments are missing in my system 

[/FONT]

---

### Post by wildmanne39 on 2020-05-12
Hello and welcome to the forum shankar-pudi3, please edit your post and remove the capitalization of every word as it is considered yelling and I am sure that is not your intention.

Thanks

---

### Post by monkeybrain20122 on 2020-05-13
I haven't used gnome shell for a while, but I remember vanilla gs doesn't have those buttons. I gather they are enabled by the Ubuntu team by default and somehow the setting changed when you upgrade. To get them back you need to install gnome-tweek-tools and enable title bar buttons.

To install

```
sudo apt install gnome-tweek-tools 
```

After installed it is a bit hard to find, open the dash(?) and look under utilities, it is called Tweaks. The search box apparently doesn't work here.

---

### Post by wildmanne39 on 2020-05-13
> To get them back you need to install gnome-tweek-tools and enable title bar buttons.

+1, I was looking at the images for gnome shell and those buttons are indeed missing in an standard install.

---

### Post by monkeybrain20122 on 2020-05-13
gnome shell by default doesn't have buttons since it tries to imitate the mobile experience, but it doesn't work with touchscreen, so go figure. :confused: I don't use it, I use unity, just log into the gnome session to answer your question.

---

### Post by shankar-pudi3 on 2020-05-14
sorry, i didnt know that

---

### Post by shankar-pudi3 on 2020-05-14
> **wildmanne39 said:**
> +1, I was looking at the images for gnome shell and those buttons are indeed missing in an standard install.


i have already installed the Tweak tool and checked the titlebar buttons. they are enabled.
i tried to apply few themes in my system and somehow seen a little progress but still icons have crosed cirlces.
pls look into the attachment

---

### Post by shankar-pudi3 on 2020-05-18
[IMG]https://photos.app.goo.gl/4jETTMHK9fFv4H2f6[/IMG][SOLVED]
I have found the issue is with > gsettings-desktop-schemas
so i reinstalled that so that broken packages overwritte. and it worked.
after that i have done 
***sudo apt-get upgrade ***
and things finally starts working
Thank you.

---

