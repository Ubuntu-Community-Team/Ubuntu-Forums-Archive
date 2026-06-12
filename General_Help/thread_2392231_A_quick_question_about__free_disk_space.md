---
title: "A quick question about  free disk space"
date: 2018-05-18
forum: General Help
---

### Post by phanhuyen345 on 2018-05-18
Hi All 
		
		Couple weeks ago I had a half of my disc free, but I found today that there is no space(see the system info below). I did not save/create any big files, so it is not clear where the space disappeared. 
		
		My disc is 450G, Home directory is 190G, Root in 252G. However, I do not understand why root is so big. There are no any big folders in it. Except Home, all other folders together are not more than 10G. So, where these 240G are? See two attached images (baobab's result and folders sizes).
		
		Could you please advise what happened and how to free space. I am not very advanced linux user (just use it to run my software), please send me simple instructions. 
		
		Thakyou!!! 
		Cheers. 
		
		plasmashell 5.6.90 
		
		Qt: 5.5.1 
		
		KDE Frameworks: 5.21.0 
		
		Konsole: 15.12.3 
		
		
```

luda@luda-Vostro-V131:~$ sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
12K /home/luda/.local/share/Trash
4.0K /home/luda/.local/share/Trash/files
4.0K /home/luda/.local/share/Trash/info
		
luda@luda-Vostro-V131:~$ df -h
Filesystem Size Used Avail Use% Mounted on
udev 2.9G 0 2.9G 0% /dev
tmpfs 588M 8.6M 579M 2% /run
/dev/sda1 453G 423G 7.4G 99% /
tmpfs 2.9G 92K 2.9G 1% /dev/shm
tmpfs 5.0M 4.0K 5.0M 1% /run/lock
tmpfs 2.9G 0 2.9G 0% /sys/fs/cgroup
tmpfs 588M 16K 588M 1% /run/user/1000
luda@luda-Vostro-V131:~$ sysinfo:/
```

---

### Post by leunam12 on 2018-05-18
Use the Disk Usage Analyzer to see what's eating up all that space.

---

