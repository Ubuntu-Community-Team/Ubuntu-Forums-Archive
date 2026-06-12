---
title: "Backup Settings,  For noobs!"
date: 2007-09-29
forum: General Help
---

### Post by juantastico on 2007-09-29
Dear all,

Hi i am new to Ubuntu (5 days old), i n the past 5 days i have reinstall Ubuntu like 7 times due to my noobeness this program :). However, today i am very happy with my current settings: i got to run Compiz like a dream, wireless, Skype, etc. And i will hate my self if  i have o reinstall Ubuntu due to my inexperience while truing to learn. is there a way to back up my current settings, so if i mess with something i do not have to reinstall Ubuntu again?

I know that there is a solution of  backing up the whole system if so can you explain in very simple terms. Remember i am a complete noob :)


Cheers

---

### Post by por100pre1 on 2007-09-29
Install Grsync. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo aptitude install grsync
```

Once installed open it in** Applications> Internet> Grsync**.

In source and destination the first line is the source /home/your-user-name.
In source and destination the second line is for the destination, use an external drive or other partition.
Check **Preserve time, Verbose and Show transfer progress**. Leave the rest unchecked.
Execute. Repeat when needed.

Hope it helps. :)

---

### Post by lowlux2gmail.com on 2007-09-29
that thing deleted everything.

---

### Post by por100pre1 on 2007-09-29
> **lowlux2gmail.com said:**
> that thing deleted everything.

The source goes above, destination below!!!  How did you do it? I truly regret any problems you are experiencing. :(

---

### Post by por100pre1 on 2007-09-29
Here's my grsync window:

[IMG]http://img299.imageshack.us/img299/9775/grsyncjs8.png[/IMG]

---

### Post by malel on 2007-09-29
I have just installed 'grsync' and it has worked okay for me .I have been looking for something like this for a long time . Is there a way to set it so that it can be run say once a week or month .

Rgds

---

### Post by g2g591 on 2007-09-30
id say "Delete on destination" is the problem just by looking at that, it sounds like that option deletes the orrigonal file once it backs up

---

### Post by juantastico on 2007-09-30
thanks very much for your help guys i will try these tips tomorrow
:):guitar:

---

### Post by por100pre1 on 2007-09-30
> **g2g591 said:**
> id say "Delete on destination" is the problem just by looking at that, it sounds like that option deletes the orrigonal file once it backs up

No, it deletes the file in destination once it is no longer in the original. It is likely that the poster confused source and destination folders. I'll remove that setting anyway.

---

### Post by lowlux2gmail.com on 2007-09-30
seems it didn't delete anything... 

what does it do? :confused:

---

### Post by tech9 on 2007-10-01
> **juantastico said:**
> Dear all,

Hi i am new to Ubuntu (5 days old), i n the past 5 days i have reinstall Ubuntu like 7 times due to my noobeness this program :). However, today i am very happy with my current settings: i got to run Compiz like a dream, wireless, Skype, etc. And i will hate my self if  i have o reinstall Ubuntu due to my inexperience while truing to learn. is there a way to back up my current settings, so if i mess with something i do not have to reinstall Ubuntu again?

I know that there is a solution of  backing up the whole system if so can you explain in very simple terms. Remember i am a complete noob :)


Cheers

Try these commands...

**To backup:**

[COLOR="Blue"]tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /[/COLOR]

**To Restore:**
[COLOR="blue"] tar xvpfz backup.tgz -C /[/COLOR]

excluding the boot dir and fstab file will give you the ability to restore all your data/settings on a new partition

Hope this helps:

Ein Prosit :-)

---

