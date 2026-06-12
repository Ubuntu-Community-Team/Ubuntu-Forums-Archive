---
title: "Grub Customizer"
date: 2014-06-22
forum: General Help
---

### Post by ev-bacon on 2014-06-22
Hello again.

I downloaded and installed the [Grub Customizer]("https://launchpad.net/grub-customizer") tool, and everything looks fine in the preview.  

Here's some screenshots:
[LIST]
[*][http://i.imgur.com/VVdns4A.png](http://i.imgur.com/VVdns4A.png)
[*][http://i.imgur.com/Tl1JcC9.png](http://i.imgur.com/Tl1JcC9.png)
[*][http://i.imgur.com/tBYRt3u.png](http://i.imgur.com/tBYRt3u.png)
[/LIST]

My background image is saved to and named /home/pictures/Enterprise in a Bottle/Purple-Bottom-Right.png

That all looks fine to me, but when I went to test it with [Grub-Emu]("http://packages.ubuntu.com/lucid/grub-emu"), I horrified to see that it will look like this monstrosity:
[LIST]
[*][http://i.imgur.com/ejBa8Vv.png](http://i.imgur.com/ejBa8Vv.png)
[/LIST]


So, my question to all of you is how can I fix my Grub so it will actually look like the one I designed with Grub-Customizer?

In the meantime, would you assume it's safe to shutdown and restart my computer and still be able to boot to both my Ubuntu and Windows HDDs, even though the Grub-Loader is super-duper ugly?

Thanks a lot, I appreciate any advice you can give me!

---

### Post by grahammechanical on 2014-06-22
Is it safe to re-boot? That can only be your decision. No one else can take responsibility for the modifications that you are making. I would say that the emulator may not have enough system memory allocated to it so as the correctly emulate how that image file will look when you re-boot. I think that you are asking grub-emul to do more than it was intended to do.

> [COLOR=#333333][FONT=Ubuntu]It is only provided for debugging purposes.[/FONT][/COLOR]

I do not think that "debugging" is the same as "preview."

Regards.

---

### Post by oldfred on 2014-06-22
I have not paid attention to fonts in grub. But it looks like you are using a special font that then grub may not have available?

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

