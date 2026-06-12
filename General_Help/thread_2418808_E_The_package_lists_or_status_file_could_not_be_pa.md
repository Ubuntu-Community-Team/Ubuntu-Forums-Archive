---
title: "E: The package lists or status file could not be parsed or opened."
date: 2019-05-11
forum: General Help
---

### Post by brkysnol on 2019-05-11
[COLOR=#000000]I got this error when trying to update - can anyone help please 
[/COLOR]
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: IO Error saving source cache
E: The package lists or status file could not be parsed or opened.


I tried them but it didn't work. I lost access to Wordpress admin panel. These were after Fio installed

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

---

### Post by cruzer001 on 2019-05-11
I thought this needed to be done recursively.
```
sudo rm /var/lib/apt/lists/* -r
```
But seems you have bigger problems.
> E: Write error - write (28: No space left on device)
Is your disk full?  Whats the output of:
```
df -h
```

---

### Post by hgkrug1 on 2019-06-20
I have the same issue.  Ubuntu 19.05 server installed on PC.  When I try to update, I get the same message. 

Any suggestions on how to solve this?
Thanks!
Gert Kruger

---

### Post by hgkrug1 on 2019-06-20
I found the solution as a combination of [https://www.reddit.com/r/Ubuntu/comments/abj80y/ubuntu_running_out_of_disk_space_new_space_not/](https://www.reddit.com/r/Ubuntu/comments/abj80y/ubuntu_running_out_of_disk_space_new_space_not/) and [https://askubuntu.com/questions/1111887/insufficient-free-space-xxx-extents-needed-but-only-0-available](https://askubuntu.com/questions/1111887/insufficient-free-space-xxx-extents-needed-but-only-0-available) 

This comand did not work (sudo lvextend -l +15103 /dev/ubuntu-vg/ubuntu-lv), as there was no free space.
So the command that I had to use was: 

sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv

This was followed by: sudo e2fsck -f /dev/ubuntu-vg/ubuntu-lv

and:  
sudo resize2fs /dev/ubuntu-vg/ubuntu-lv

Best wishes
Gert Kruger

---

