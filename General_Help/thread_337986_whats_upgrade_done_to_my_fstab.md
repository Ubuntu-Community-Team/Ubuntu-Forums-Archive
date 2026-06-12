---
title: "whats upgrade done to my fstab"
date: 2007-01-13
forum: General Help
---

### Post by glenndavy on 2007-01-13
Hi 2 questions about fstab...

1) at upgrade to edgy time ubuntu changed my fast so that instead of /dev/hda it read UUID=...  .Now thats been remarked out and replaced with something like:

/dev/hda1 = /var/run/drives/ata-disk-hda1 ....

*as well* as mounting the non-uuid form (/dev/hdx) on its orginal mount.

can someone tell me what this is about? is it the result of a certain package? I have another 3 ubuntu edgy machines, none of which have 'reconfigured themselves' to this curious state?

2) The swap volume has changed to from swap to swsup - now I cant s2disk suspend, nor can i get it to work as a swap volume.I cant seem to find much information on swsup - anyone know about this?

glenn

---

### Post by dcstar on 2007-01-13
> **glenndavy said:**
> Hi 2 questions about fstab...
.......
2) The swap volume has changed to from swap to swsup - now I cant s2disk suspend, nor can i get it to work as a swap volume.I cant seem to find much information on swsup - anyone know about this?

glenn

The swap should be type "swap" or "sw", change it to one of those.

---

### Post by taurus on 2007-01-13
Either post your /etc/fstab here

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```
or the entry for your swap should look like this, assuming it's /dev/hda5.

```
/dev/hda5   none   swap   sw   0   0
```

---

### Post by glenndavy on 2007-01-13
he david - will do. any idea what might have changed it? and what I might be breaking in the process of putting it back?

---

### Post by bodhi.zazen on 2007-01-13
> **glenndavy said:**
> Hi 2 questions about fstab...

1) at upgrade to edgy time ubuntu changed my fast so that instead of /dev/hda it read UUID=...  .Now thats been remarked out and replaced with something like:

/dev/hda1 = /var/run/drives/ata-disk-hda1 ....

*as well* as mounting the non-uuid form (/dev/hdx) on its orginal mount.

can someone tell me what this is about? is it the result of a certain package? I have another 3 ubuntu edgy machines, none of which have 'reconfigured themselves' to this curious state?

2) The swap volume has changed to from swap to swsup - now I cant s2disk suspend, nor can i get it to work as a swap volume.I cant seem to find much information on swsup - anyone know about this?

glenn

LOL glenndavy !

Yes fstab changed to UUID

Here is a link on UUID:

[http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

Why you ask ? Well I don't know :(

You can list your partitions by uuid via:

```
blkid
```

or 

```
ls /dev/disk/by-uuid -l
```

Watch out, the uuid will change if you re-format the partition :p

You can revert fstab to 

/dev/hdax bla bla bla

or 

LABEL=use_a_label_here

Not sure if it helps, but information never hurts :)

---

### Post by glenndavy on 2007-01-14
hi bodhi zazen
the UUID wasnt the puzzling thing (well it is, but its not what I was asking), it was  the mounting of /dev/hdX on /var/run/ata-drives/hdaX, and the change of 'swap' to 'swsup' that puzzles me?

I should post the fstab as mentioned above, but not in position to at the momemnt
any ideas?

thanks glenn

---

### Post by bodhi.zazen on 2007-01-14
Sorry about that.

I am not sure about your swap.

Here is my lines from fstab on Feisty:
> # /dev/sda13
UUID=d3adc651-c34b-4598-8ff7-1214ff859204 none            swap    sw              0       0

I do not know much about swsup, apparently it has something to do with suspend mode.

Here is a "how-to" I found on Ubuntu but I am not sure if it helps you much :(

I did not see much on configuration of swap

[http://ubuntuforums.org/showthread.php?t=75443](http://ubuntuforums.org/showthread.php?t=75443)

---

