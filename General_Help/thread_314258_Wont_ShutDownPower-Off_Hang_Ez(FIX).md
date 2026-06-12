---
title: "Wont ShutDown/Power-Off Hang Ez(FIX)"
date: 2006-12-07
forum: General Help
---

### Post by Kross on 2006-12-07
I'm Sorry I can't find that link..SO I will just repost here...

[COLOR="Red"]I upgraded an (old) system from sarge to etch, which was impressive, almost 
everything worked out of the box as in sarge (only better due to new 
software:-)

The only flaw I saw is that after running "shutdown -h now" power is not shut 
down any more.

Since the system is old, it uses apm and after googleing for the problem, I 
added

append="acpi=off apm=power_off"

to /etc/lilo.conf and 

[COLOR="Green"]apm power_off=1

in /etc/modules


[/COLOR]
Now, this powers off the system again at the end of shutdown.

Not sure if there is an easy way to avoid that others have to search for this 
information as well. Little effort would be to add this to the release 
notes... and a big benefit for the guys with old hardware who read release 
notes ;-)[/COLOR]

Now I use grub so acpi=off apm=power_off in my /boot/menu.lst file.

AS such =
## ## End Default Options ##
[COLOR="Red"]
title		Debian GNU/Linux, kernel 2.6.18-3-k7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.18-3-k7 root=/dev/hda2 ro [COLOR="Green"]acpi=off apm=power_off[/COLOR]
initrd		/boot/initrd.img-2.6.18-3-k7[/COLOR]

From what I can understand this is a command problem within the new
 kernels dealing with Power Management. eg..ACPI.,and believe this 
force it to use APM.

Now It is Also For me to say that there were a few poeple whom this
 did not work..There was a restore in this case someone had this
 problem posted,,But I no longer have the link.

I also Don't not think this is for Laptops, for I think they 
need ACPI for the battery power. And this disables that.

If anyone has this Not work..and Knows this restore please post.

And good luck.

<=Kross=>

---

### Post by Kross on 2006-12-07
I Have found the first link..

If you have a problems,,,with this aka.fix.

check this out..
[http://ubuntuforums.org/showthread.php?t=298595&highlight=shutdown]("http://ubuntuforums.org/showthread.php?t=298595&highlight=shutdown")
 

Thanks.

<=Kross=>

---

### Post by Kross on 2006-12-29
bump.

---

### Post by Kross on 2007-01-08
> **Kross said:**
> bump.

bump

---

