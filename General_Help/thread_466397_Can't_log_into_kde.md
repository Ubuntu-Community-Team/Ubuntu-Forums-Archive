---
title: "Can't log into kde"
date: 2007-06-06
forum: General Help
---

### Post by Princey on 2007-06-06
Hi all

I live in an area that's prone fo frequent power outages. Lately, we're getting them twice or more a week. Yesterday, when I got home from work, I discovered there was no power. Upon return, I booted up normally save for a few error messages of files not being 'clean'. I searched for the UPS software I once used using 32 (I run 64 bit now) and installed. Everything went fine. I rebooted to make sure things worked well, and sure did. Booted back up safely and I was contented. I shut down the comp on my way out this morning to work but forgot a project I had to copy to my thumb drive, booted back up and I was presented with a message after logging in. > can't start kstartupconfig. check your installation Ok, wasn't the first time I saw that message, so I booted into safe mode and tried the normal trick that works ```
sudo chown -R princey:users /home/princey
``` and hit the enter key. After typing my password, I got an error message > chown error can't find /home/princey
file/directory cannot be found

Now, that shook me off a bit so I tried the next trick I know would work ```
sudo chown -R princey:users .kde
``` and got the same error message. I tried substituting 'users' with 'princey', but nothing worked. I booted back to the LiveCD and searched the forums. One person got theirs working with ```
sudo rm -r /home/princey/ .kde/
``` 

That appeared to have done something, but couldn't log in. Finally, I tried typing > kstartupconfig in the terminal to see if I'd get any error messages. I got the following: > trying to create local folder //.kde/share: permission denied so I tried doing a listing of my drives seeing that /home resides on a partition by itself. Sure, it's listed. But when I do the ```
ls
``` command I do see the home directory. But changing to that directory, there's nothing in there. Apparently, it's not using the /home partition but created a /home directory on the /boot partition.

Using Knoppix, my home partition is accessable. I can access any file there on that partition, how do I get Kubuntu to see my home partition as the right /home directory?

---

### Post by Princey on 2007-06-06
Update:

Finally got it working. Turns out that my fstab file got messed up. Had to re-enter the line with the /home partition after first getting the uuid# for it.

---

### Post by Crafty Kisses on 2007-06-06
> **Princey said:**
> Update:

Finally got it working. Turns out that my fstab file got messed up. Had to re-enter the line with the /home partition after first getting the uuid# for it.

If you have any other questions, remember to post back. :p

---

