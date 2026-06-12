---
title: "[SOLVED] Can't load Facebook's website on Ubuntu..."
date: 2007-10-31
forum: General Help
---

### Post by jonathanmotes on 2007-10-31
Hello,

I cannot seem to get Facebook to work on Ubuntu, but it works well with Windows on the same network. I get the "Facebook | Home" title in the Firefox tab, but that is all. The Circle next to the title keeps spinning (indicating it's trying to access the website). At the bottom it says "waiting for static.ak.facebook.com...."

I've been trying to use Facebook on Ubuntu for about two weeks, so its not something random. I've also let it set for at least 10 minutes at a time in hopes that it would load, to no avail.

Has anyone else had this problem? 

Thanks,
Jonathan

---

### Post by ddrichardson on 2007-11-01
I've never had any problems, try entering about:config in the address bar and change network.dns.disableIPv6 to true, see if it's related to IPv6.

---

### Post by jonathanmotes on 2007-11-02
> I've never had any problems, try entering about:config in the address bar and change network.dns.disableIPv6 to true, see if it's related to IPv6.

Thanks for the reply! However, I have already done this in order fix connection speeds with a Belkin wireless router, so I don't think that is the problem.

---

### Post by jonathanmotes on 2007-11-02
Anyone?

---

### Post by Sef on 2007-11-02
I would try the Opera browser and see if it works.    It is in Applications > Add/Remove.

---

### Post by dulbirakan on 2007-11-02
I had some problems in Gutsy 64bit, they were related to java I guess. I never sorted them out as I switched back to 32bits.

---

### Post by jonathanmotes on 2007-11-03
> I would try the Opera browser and see if it works. It is in Applications > Add/Remove. Well, I tried to install Opera, but I am getting a VERY weird message (see the attachment), and I am using the 32-bit version of Ubuntu (although I have an AMD 64-bit processor). This is really strange, especially considering that I have used Opera before (on Feisty) with the same computer.

---

### Post by minus198 on 2007-11-04
> **jonathanmotes said:**
> Hello,

I cannot seem to get Facebook to work on Ubuntu, but it works well with Windows on the same network. I get the "Facebook | Home" title in the Firefox tab, but that is all. The Circle next to the title keeps spinning (indicating it's trying to access the website). At the bottom it says "waiting for static.ak.facebook.com...."


Good for you.. 

That page is friggin sick.. And I thought google tried to become the world dominator's...

---

### Post by jonathanmotes on 2007-11-05
Fixed the problem! After reading dulbirakan's post, I decided to look at my installed Java software. I noticed that "Sun Java 5.0 Browser Plugin" was available, so I installed it, and it works now! It's strange that it works for some people (that I'm assuming don't have the plugin), but not others.

Thanks for everyone's help!

---

