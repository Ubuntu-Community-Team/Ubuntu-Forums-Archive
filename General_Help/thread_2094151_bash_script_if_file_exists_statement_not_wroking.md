---
title: "bash script if file exists statement not wroking"
date: 2012-12-13
forum: General Help
---

### Post by sirbow2 on 2012-12-13
im working on some bash scripts that run on logon/off and backup the resume data for uTorrent so that it automatically copies the resume data to the other OS i boot into and resumes the torrents where i left off ( i have a quad boot :D). im currently working on the Ubuntu on/off scripts. i have Ubuntu 12.04.

the problem is that i cant get the if file exists part to work:
```
if [ -f "/opt/utorrent-server-v3_0/resume.dat" ];
```
i know *"/opt/utorrent-server-v3_0/resume.dat"* exists as i get command not found in terminal. It always goes to the else, so im pretty sure something is wrong with the file exists part. what do you guys think?

Thanks!

```
if [ -f "/opt/utorrent-server-v3_0/resume.dat" ]; #if it exists 
	then 
		#copy currrent resume to the Data partition
		cp "/opt/utorrent-server-v3_0/resume.dat" "/media/Data/uTorrentBack" 
		cp "/opt/utorrent-server-v3_0/resume.dat.old" "/media/Data/uTorrentBack"
		#copy all .torrent files to the Data partition
		cp "/opt/utorrent-server-v3_0/"*.torrent "/media/Data/uTorrentBack"
	#else
		zenity --info --text="uTorrent resume files not found! \n uTorrent not installed?" #make a pop-up alert!
fi
```

PS: i couldn't post in the dev + program forum below, sorry :(

---

### Post by papibe on 2012-12-13
Hi sirbow2.

A few ideas:

If you don't have permissions to access the file (you can't 'ls' it), the 'if' test will fail.

-f is to test for a regular file. What kind of file is resume.dat?

You can also try '-e' as it only cares about if it exits (no problems with directories, devices, etc).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by drmrgd on 2012-12-13
In your above code snippet, you have the 'else' commented out.  Is it that way in your script?  If so, that's why the 'else' is executing; there really is not 'else' in that script :D

---

### Post by sirbow2 on 2012-12-13
haha, wow, sorry about that. the # would be it. 

works great :P

---

