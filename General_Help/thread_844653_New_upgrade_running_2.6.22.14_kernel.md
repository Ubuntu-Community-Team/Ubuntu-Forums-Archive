---
title: "New upgrade running 2.6.22.14 kernel???"
date: 2008-06-29
forum: General Help
---

### Post by pikaia on 2008-06-29
Hey everyone.

I've done some searching and haven't found anywhere that solves this issue.  Its usually just some setting someone forgot.  

I just upgraded from Gutsy, I've been running Linux (ubuntu) for about 9 months.  Everything seemed to go smoothly but when I rebooted, my nvidia card refuses to run.  Which I think is related to another problem I noticed after the tenth time I rebooted trying to fix it.  It has me running an old Gutsy kernel 2.6.22.14.  I went through my /boot/grub/menu.lst file and NONE of the hardy kernels are there.  But in Synaptic I think I've got them installed.  2.6.24.19 is installed.  

Where is it?  How do I use it?  Can I use it.  I'm getting lots of issues.  From the graphics to generally crappy internet reliability.  (1 in 5 page loads errors out now).

Please.  I've searched for "How to upgrade kernel"... and I get some things about compiling custom kernels, but nothing I'm looking for.  I've tried this with varying wordings and still feel completely frustrated.

Thanks again for anything.

---

### Post by bpl07 on 2008-06-29
You probably just need to edit your menu.lst.  Check /boot to make sure the kernel image and stuff is there, then edit one of the entries (or copy and paste to make a new entry) to make a new 2.6.24.19 entry.  Whenever I update the kernel I always choose to keep the local menu.lst in place so I can go back and manually edit the list myself.  It's a good idea to keep at least one kernel that you know works in the list, even if it's pretty old.

Should look something like this:
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ddb62347-733c-48ce-b347-d447b119f483 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

---

### Post by pikaia on 2008-06-29
This is where my noobishness comes through.  I checked my /boot/grub/menu.lst and there is NO Hardy (newer) kernels listed.  

I tried a sudo nano /boot to see if that was anything and of course its not.  So how do I find whether or not its 'there?'  I see that its been installed in synaptic... but don't know where else to look.

Thanks for the super quick response.

EDIT:  Ok.  I cut and pasted yours and then tried it... a no go.  Then I went and saw that each of the previous version of my kernel had the same root location and so I just transcribed that into the grub and now it all works fine.

Thanks.

---

