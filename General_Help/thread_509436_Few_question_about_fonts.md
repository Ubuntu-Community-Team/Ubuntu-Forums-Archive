---
title: "Few question about fonts"
date: 2007-07-25
forum: General Help
---

### Post by swarog on 2007-07-25
Hi everybody!

I've been using my desktop with Ubuntu 6.06 for some time, and I've setup TrueType fonts there and managed to make it look fine for me. And now I've installed Ubuntu 7.04 on my laptop and can't do the same thing to my new installation. At the moment I've only installed msttcorefonts and accompanying packages. So I have the following questions:

1) Are there any severe changes in fonts configuration system in 7.04 as compared with the 6.06's one, so I can just copy-paste all configuration files? And if there aren't, what are those files? 

2) Is there a full document describing font customization in Ubuntu?

Thanks for your help!

---

### Post by linuxwizard on 2007-07-25
I only know of this one but not sure if it will help.

[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

---

### Post by stchman on 2007-07-25
> **swarog said:**
> Hi everybody!

I've been using my desktop with Ubuntu 6.06 for some time, and I've setup TrueType fonts there and managed to make it look fine for me. And now I've installed Ubuntu 7.04 on my laptop and can't do the same thing to my new installation. At the moment I've only installed msttcorefonts and accompanying packages. So I have the following questions:

1) Are there any severe changes in fonts configuration system in 7.04 as compared with the 6.06's one, so I can just copy-paste all configuration files? And if there aren't, what are those files? 

2) Is there a full document describing font customization in Ubuntu?

Thanks for your help!

You should be able to copy the configuration files into your /etc/fonts and restart the workspace.

You can also install some fonts into in the /usr/share/fonts/truetype and create a folder.  Once that is dont do a:

```

sudo fc-cache -f -v

```

That will add the fonts to your apps.

---

