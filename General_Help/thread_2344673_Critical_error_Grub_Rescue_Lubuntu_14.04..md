---
title: "Critical error Grub Rescue Lubuntu 14.04."
date: 2016-11-27
forum: General Help
---

### Post by Portaro on 2016-11-27
Is very strange my pc works very well yesterday  I work in him in the afeternoon but when I connect the pc at night the pc dont boot and present following error message &#8594;

error: file '/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue>

I dont do any update or upgrade on the system and at this time I cant find any solution.

What can I do?

My intention is to preserve this system , I dont like if I need to reinstall the system because I already have the custom packages and configs .

This worry me.

Thanks for any help.:popcorn:

---

### Post by Portaro on 2016-11-27
Nice other problem &#8594;

I make a live -cd and now I have access to the / system but when I try to mount it I receive other message that is other big problem &#8594;
erro mounting /dev/sda5 ... exited with non-zero exit status32:mount : ...

I open a terminal and I use this command :

$ sudo e2fsck -f /dev/sad5 
And this find many blocks corrupted and then question if I want to correct it (there are many blocks corrupted)
Then when this finish I already can mount the system.

Ref to the content Tha I follow to find a solution (partial) &#8594;
[URL="https://ubuntuforums.org/showthread.php?t=839579"]https://ubuntuforums.org/showthread.php?t=839579

[https://ubuntuforums.org/showthread.php?t=1245536&p=7822694#post7822694](https://ubuntuforums.org/showthread.php?t=1245536&p=7822694#post7822694)
[/URL]

---

### Post by Portaro on 2016-11-27
Solved &#8594; I only have do the above command and for me now the system boots well .
Thanks for the help.

---

### Post by ajgreeny on 2016-11-27
You should probably go to the Disks application in your system and check if there are any physical errors showing in the Disk or partition sda5 that gave you the error.

Disks do have a limited life and right now might be the time to backup and replace the disk if it shows many bad sectors or similar problems.

---

