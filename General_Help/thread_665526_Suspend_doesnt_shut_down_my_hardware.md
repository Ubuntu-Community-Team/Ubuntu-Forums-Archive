---
title: "Suspend doesnt shut down my hardware"
date: 2008-01-12
forum: General Help
---

### Post by NoSmokingBandit on 2008-01-12
I just installed Gusty yesterday, i figured i've give it another go after some updates were made and all that jazz. Anywho, my suspend doesnt seem to be working. It goes through the whole fading out process and stuff and gives me the login box that it gives when you just lock the screen. None of my hardware shuts down or anything. When i log back in i get the message in the bottom right that says 
"Your computer failed to suspend. Check the help file"
...or something like that.
So i search the help file and it says that the most common problem is that i dont have permission to suspend the computer. But it doesnt tell me how to fix it! So i went into user accounts but i really have no idea what im doing.
Im running Gusty, fully updated as of yesterday, on a dell optiplex gx240. Intel cpu, nvidia video card. I think thats all the info thats pertinent. Let me know if you need more info. Thanks!

Sidenote:
After i get that fixed though, is there a way to diable the mouse from waking up my pc? That way if i bump the desk my computer doesnt start up? Thanks

---

### Post by NoSmokingBandit on 2008-01-13
anyone?

---

### Post by peterthewolf on 2008-05-20
Try this

     Replace network manager with wicd (just search wicd in google).

     Add acpi=force to the kernel line in /boot/grub/menu.lst

---

