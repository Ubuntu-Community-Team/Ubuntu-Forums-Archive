---
title: "Disk Manager"
date: 2006-08-05
forum: General Help
---

### Post by xander848 on 2006-08-05
When I go to System ->Admin -> Disks I just get a blank window. When i try to exit nothing happens and then it tells me that its not responding.

Im pretty sure its called "disks-admin" and I looked in synaptics for it but nothing. Any ideas what to do?
Edit/Delete Message

---

### Post by tonyr1988 on 2006-08-05
What happens if you open up a Terminal and type "sudo disks-admin"? Any errors?

---

### Post by xander848 on 2006-08-05
Ok at first I thought nothing happened. I left the terminal open by mistake and like 3 minutes later it popped up.  I then tried to do the same for clicking "disks" and after 2-3 minutes the window actully displayed the proper contents. 

I guess its not a huge deal because i can still access it if i need to but what is up with the extremly long loading time?

---

### Post by siucdude on 2006-10-12
Same problem here but when I try the sudo disks-admin i get command not found

can someone please help.

Thanks

---

### Post by DarkN00b on 2006-10-12
Nope, sorry. It pops up in about 5 secs for me.

---

### Post by clark3rd on 2006-10-21
> **tonyr1988 said:**
> What happens if you open up a Terminal and type "sudo disks-admin"? Any errors?

yup, "disks-admin: command not found" is it gone from edgy? What can I use in its place?

---

### Post by ales on 2006-10-28
> **clark3rd said:**
> yup, "disks-admin: command not found" is it gone from edgy? What can I use in its place?

I have the same problem. More I can't make Ubuntu Edgy to see my second data HDD. It shows me the drive where it is installed , windows drive I mounted with help on the net but the second IDE Drive it doesn;t see. The second drive has linux file system. ANy idea how to make edgy to see it?

---

### Post by beerfan on 2006-10-28
> **clark3rd said:**
> yup, "disks-admin: command not found" is it gone from edgy? What can I use in its place?

See the known issues sticky thread. Disk manager was removed and there is no replacement that anyone has found.

---

### Post by sunfisher on 2006-10-28
Endeavour2 seems to be working well in Xubuntu 6.10. Anyone else using it?

---

### Post by offbyte on 2006-11-23
> **clark3rd said:**
> yup, "disks-admin: command not found" is it gone from edgy? What can I use in its place?

i confirm that any sujestions on replacements for edgy?

---

### Post by fragos on 2006-11-23
Use Synaptic to install pysdm, Storage Device Manager.  Not quite the same but similar and may do what you need.  For whatever reason disk-admin is gone.

---

