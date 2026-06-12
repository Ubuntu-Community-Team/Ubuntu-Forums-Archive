---
title: "[SOLVED] cryptsetup-update breaks boot - who can help?"
date: 2007-03-13
forum: General Help
---

### Post by loko on 2007-03-13
hello,

yesterday i updated cryptsetup to 2:1.0.4+svn26-1ubuntu1~edgy1.

after reboot i couldn't mount my encrypted home-partition anymore.

even /etc/init.d/cryptdisk start doesn't do anything.

so i switched back to 1.0.3 version, but i still have a problem.

the prompt for the password doesn't appear anymore.

i can see the error-message: "enter passphrase: command failed: key reading error"

so at every boot i have to login as root, start cryptdisks by hand.

what has the new update break in my system?

---

### Post by mish on 2007-03-13
Same problem here.  I've stuck with the new version.  I did try doing the manual edits to /lib/cryptsetup/cryptdisks.functions suggested in [https://launchpad.net/upstart/+bug/62751](https://launchpad.net/upstart/+bug/62751) but they didn't work.

/etc/init.d/cryptdisks start  did not help (and neither did restart)

Eventually I ran cryptsetup from the command line and got running.  

But no passphrase prompt ever appears for me :(

---

### Post by mish on 2007-03-13
Oh yeah, if anyone needs them, the commands I had to run to set up my encrypted partition and mount it were

# /sbin/cryptsetup create cvar /dev/hda5
# /bin/mount -t ext3 /dev/mapper/cvar /var

Obviously you'll need to put your own partitions and /dev/mapper names in there.  and 

# fdisk -l

is a useful command to list your partitions if you forget which is which.  Or look in /etc/crypttab and /etc/fstab for the info you need.

---

### Post by onovy on 2007-03-14
you must edit /etc/crypttab and add to last row: 'vol_id'
in previous version this was default, now you must explicit add it.

my crypttab:
onovy@lajka:~$ cat /etc/crypttab
# <target device> <source device> <key file> <options>
crypt /dev/hda2 none vol_id

---

### Post by loko on 2007-03-14
> **onovy said:**
> you must edit /etc/crypttab and add to last row: 'vol_id'
in previous version this was default, now you must explicit add it.

my crypttab:
onovy@lajka:~$ cat /etc/crypttab
# <target device> <source device> <key file> <options>
crypt /dev/hda2 none vol_id

thank you onovy,

this is the solution.

---

### Post by loko on 2007-04-11
i now installed feisty and it seems that there is no need to add vol_id anymore. but i got another problem.

The boot-splash switches to console, where i can see "Starting Cryptodisks" (or similar message) but it didn't go automatically to the next step, "Enter Passphrase".
I always have to press a button (not enter, only the letters do it) then the console switch to the message "Enter Passphrase" and now i can enter the password. Without pressing a letter-button, nothing happens and it waits forever.

can somebody confirm this behavior and is there a workaround?

---

### Post by loko on 2008-03-10
> **loko said:**
> i now installed feisty and it seems that there is no need to add vol_id anymore. but i got another problem.

The boot-splash switches to console, where i can see "Starting Cryptodisks" (or similar message) but it didn't go automatically to the next step, "Enter Passphrase".
I always have to press a button (not enter, only the letters do it) then the console switch to the message "Enter Passphrase" and now i can enter the password. Without pressing a letter-button, nothing happens and it waits forever.

can somebody confirm this behavior and is there a workaround?

Well this is a problem with /dev/random. here is something more about it.

[https://bugs.launchpad.net/upstart/+bug/62751]("https://bugs.launchpad.net/upstart/+bug/62751")

---

