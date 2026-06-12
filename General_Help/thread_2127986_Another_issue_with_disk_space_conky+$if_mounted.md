---
title: "Another issue with disk space conky+$if_mounted"
date: 2013-03-21
forum: General Help
---

### Post by niceshorts on 2013-03-21
Like the [old thread]("http://ubuntuforums.org/showthread.php?t=899918&p=12567401#post12567401") the problem with conky with disk space like Local Disk or Lacie Disk is still present and I have not found a solution after a lot of research on the Internet.

My little script is [here]("http://ubuntuforums.org/showthread.php?t=899918&p=12567401#post12567401")

or:

${color 33001A}${font StyleBats:size=35}G${font} Lacie${color FFFFFF}
${if_mounted /media/nili/Lacie Disk}
${color 1C1C1C}Size: ${alignr}${fs_size /media/nili/Lacie Disk}
${color 33001A}${fs_bar 3,83 /media/nili/Lacie Disk}${color}
${color 1C1C1C}Free: ${alignc}${fs_free /media/nili/Lacie Disk} ${alignr}${color 33001A}(${fs_free_perc /media/nili/Lacie Disk}%)${color}
${color 1C1C1C}Used: ${alignc}${fs_used /media/nili/Lacie Disk} ${alignr}${color 33001A}(${fs_used_perc /media/nili/Lacie Disk}%)${color}
${else}${color 1C1C1C}Disk: Not mounted${color}
${endif}

[IMG]http://img845.imageshack.us/img845/3973/screenshotarea201303201.png[/IMG]


The problem as is described above is the same for me, my external disk  Lacie Disk has this space between lacie and disk which creates problem  to display info when the disk is mounted. "To remember, the disk Lacie  is mounted but show not mounted because of the Space on the disk name".

while on Disk Toshiba plus Seagate with the same code work OK, because Toshiba and Seagate doesn't have space. 
So how to fix the problem of space on the code above?

P.S. i not want to change now the disk name, i'm too late and have the  programs that work with Lacie Disk. Tried aidenscool09 suggestion on the old thread but  none of them worked for me.

Has anyone any other ideas or solutions?
Thank you!
Regards!

---

