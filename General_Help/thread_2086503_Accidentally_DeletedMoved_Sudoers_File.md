---
title: "Accidentally Deleted/Moved Sudoers File"
date: 2012-11-21
forum: General Help
---

### Post by amanisdude on 2012-11-21
Hi everyone. It seems that I've made a very stupid mistake.

So I've been migrating and symlinking system files on my server for the purposes of easier backup. (Don't ask. I know it's a bad idea.) Anyway, I managed to issue a command something like this and now I no longer have sudo access. ^_^"

```
sudo mv /etc/sudoers /systemdata/etc/sudoers && sudo ln -s /systemdata/etc/sudoers /etc/sudoers
```

Like I said, it's a very STUPID mistake for obvious reasons. (I should have first become root. :D)

At any rate, is there a way to link to the new sudoers file or restore the old sudoers file without root access and without having to physically go to my server and booting into recovery mode? (My hope is actually 'no' for security reasons, but 'yes' for convenience. :D)

Thanks for any help, and please spare me the lecture on wanting to move sudoers in the first place. ^_^"


-***amanisdude***
_____________________

---

### Post by westie457 on 2012-11-21
Hi, not being very adventurous I have never tried to do what you have done. Best suggestion from me is in this link [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Maybe there is a better way and maybe someone who has more experience than me will be able to help.

---

### Post by amanisdude on 2012-11-21
Thanks for the quick reply, ***Westie***!

The link you posted is great! Unfortunately, my recovery mode requests a "root password for maintenance" when selecting the "Drop to root shell prompt" option. Funnily enough, I don't remember ever setting this password. Oh well. Looks like I'll have to just boot from CD.

-***amanisdude***
_________________

**EDIT:** Cancel that! Looks like I did set a root password for maintenance, so we're all good! CD not required! Still, though. One does need physical access to the server. Is there any way someone could do this without having to drive 10km or whatever? (My server is near me, so it was no problem. But for any future readers who aren't near their server, is it possible?)

---

### Post by amanisdude on 2012-11-21
Okay. So apparently symlinking sudoers instead of using an actual file in /etc **does not work**, probably for security considerations. (Sudo apparently checks to see if its an actual file.) 

Normally I would be a bit disappointed, but because sudo seems more secure, I'm extatic! So it looks like I'm going to have to hard link the sudoers file instead, and I don't mind one bit. :D Anyway, it seems that this little misadventure of mine was not a bust after all.


-***amanisdude***

---

### Post by solracer39 on 2012-11-21
> **westie457 said:**
> Hi, not being very adventurous I have never tried to do what you have done. Best suggestion from me is in this link [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Maybe there is a better way and maybe someone who has more experience than me will be able to help.

I also messed up my sudoers file, but I am unable to get the grub menu to come up when I hold shift? Any thoughts on getting the boot menu to show?

Thanks

---

### Post by amanisdude on 2012-11-30
> **solracer39 said:**
> I also messed up my sudoers file, but I am unable to get the grub menu to come up when I hold shift? Any thoughts on getting the boot menu to show?

Thanks

Hi Solracer,

Sorry for the delayed response. It may not be relevant to you anymore, but according to the [Ubuntu Grub2 Community Docs]("https://help.ubuntu.com/community/Grub2#GRUB_vs_GRUB_2"), holding down the ESC key on boot may also work. Good luck!

-***amanisdude***

---

