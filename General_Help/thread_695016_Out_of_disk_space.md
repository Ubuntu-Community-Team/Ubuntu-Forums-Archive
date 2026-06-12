---
title: "Out of disk space : /"
date: 2008-02-12
forum: General Help
---

### Post by robotclaws on 2008-02-12
Hi, I'm unable to log into my account on my computer.  it tells me that i am out of disk space and that it is unable to log in.  Since I haven't been using linux long, i don't know how to get around this.  can anyone help me?  The exact message is, "GDM could not write to your authorization file." is there a way that i can access the equivalent of safe mode so that i can free up some space?

Any help would be greatly appreciated : )

Jon

---

### Post by apetresc on 2008-02-12
> **robotclaws said:**
> Hi, I'm unable to log into my account on my computer.  it tells me that i am out of disk space and that it is unable to log in.  Since I haven't been using linux long, i don't know how to get around this.  can anyone help me?  The exact message is, "GDM could not write to your authorization file." is there a way that i can access the equivalent of safe mode so that i can free up some space?

Any help would be greatly appreciated : )

Jon

That doesn't mean you're out of disk space :) It just means there's been a permissions problem with your .ICEauthority file. Log into the 'recovery' kernel from the Grub menu (or using a livecd), go to your user's home directory, and type ```
rm .ICEauthority
``` Then reboot and try to log in again. It should work this time.

Good luck!

---

### Post by robotclaws on 2008-02-12
ok, what is the recovery kernel from the grub menu?  i really dont know enough about linux to have any business using it so i need explicit directions.

thanks
jon

---

### Post by apetresc on 2008-02-12
> **robotclaws said:**
> ok, what is the recovery kernel from the grub menu?  i really dont know enough about linux to have any business using it so i need explicit directions.

thanks
jon

Right when your computer first boots, there should be a menu listing several "kernels". If not, there should be some sort of timer that says something like "Press Esc to view boot menu" or something like that. Hit Esc and you'll get that same list of kernels.

One of the entries (probably the 2nd one from the top) will be the same as the top one but say "(Recovery Mode)" at the end. This is like Linux's "Safe Mode". Select that one and hit enter. It'll boot into the command line. Then just do
```
cd /home/MY_USER/
rm .ICEauthority
reboot
```
Then just do everything again as usual.

---

### Post by ozzyprv on 2008-02-15
I tried what AdriaP suggested. Does not work. I think my problem IS available space in the "/" partition. I should have fix it before rebooting last time.
Now I cannot get into my laptop.

I have the (alternate) CD with the flavor of Ubuntu I am using, but did not see anything there to go and increase the size of "/".

Any other idea? Please help.

Thanks in advance.

EDIT: Solved the problem using [this thread]("http://ubuntuforums.org/showpost.php?p=3788087&postcount=2").

---

### Post by Sokertes on 2008-02-15
Can you do a Ctrl+F1 to get to a console?

If so see if you can log in that way. I ran into that recently (was still logged in though) and had to run "sudo apt-get clean" then I was able to delete some iso files I created.

If there is no big files to delete you can run "sudo /usr/sbin/logrotate -f /etc/logrotate.conf" to rotate your log files (which should compress the old ones).

Then check out your /tmp dir for some straggling tmp download files hanging around. When you browse and download files the browser first puts it in /tmp dir before moving it to where you specified the download to go.

Hope that helps


Sokertes

---

### Post by mbsullivan on 2008-02-15
Hi ozzyprv,

Now that you can log in, you might want to delete some more things so that you don't just run into this problem again once your disk fills up again. An easy (though not the only)  way to find the largest files and folders on your machine is to use a command like:

```
du -a / 2>/dev/null | sort -n -r | head -n 200 | tee ~/FILE_SIZES.txt
```

This code uses du -a to get the size of all objects (ignoring error messages), sort -n -r to sort the results (largest to smallest), head -n 200 to only report the 200 largest files and folders, and tee ~/FILE_SIZES.txt to print the output both to the screen and to a file.

Also, I know that your problem WAS a full disk, but for future reference to people with similar problems... In addition to improper permissions being set for your .ICEauthority file, this problem may be caused by improper permissions for your /tmp directory.

If your harddrive is not full, try:

```
sudo -s
chown root:root /tmp
chmod 777 /tmp
```

Cheers!
Mike

---

