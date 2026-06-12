---
title: "Bash script question"
date: 2005-08-01
forum: General Help
---

### Post by xmastree on 2005-08-01
Why doesn't this work? I'm preparing to replace my webcam server, (currently running mandrake 8.0) with a different machine, and I'm putting ubuntu 5.04 on it this time.
I've copied the relevant files from the mdk system, namely sdk, which controls the camera, and the scripts I wrote to make it all happen.

The script doesn't work. :-(

The script basically does this:
Delete all photos in the camera,
take a photo,
download to the computer,
rename/resize/datestamp it,
upload to the website.

If I run the delete command in a terminal, this is the response:

```
chris@cginternet:~/camera$ /home/chris/camera/sdk-1.2.2/bin/delete -p5 -s5 -a
Aug  2 08:13:30 delete[8623]: lll     LOG   reset_camera_comms() failed ...
Aug  2 08:13:30 delete[8623]: sdk     LOG   failed to reset camera comms
delete: failed to open the camera, status -1002

```
That's what I expect, as the camera isn't yet connected. Fair enough, at least it's trying.

However, when I run the script containing that exact same line, I get this:

```
chris@cginternet:~/camera$ ./cam.sh
clear
Usage: delete [ -p port number (0-8) ] [-s baud rate (0-5) ] -n picture number
       delete [ -p port number (0-8) ] [-s baud rate (0-5) ] -a all
       delete [ -h | -? ]
take
Aug  2 08:39:15 snap[8977]: lll     LOG   reset_camera_comms() failed ...
Aug  2 08:39:15 snap[8977]: sdk     LOG   failed to reset camera comms
snap: failed to open the camera, status -1002
dump
rename
scale down
upload
chris@cginternet:~/camera$

```

Only the delete and take commands are active, all the other lines are commented apart from the echos. The delete command is responding as if the parameters aren't being passed to it. Like this:


```
chris@cginternet:~/camera$ /home/chris/camera/sdk-1.2.2/bin/delete
Usage: delete [ -p port number (0-8) ] [-s baud rate (0-5) ] -n picture number
       delete [ -p port number (0-8) ] [-s baud rate (0-5) ] -a all

```
Although the 'take' command is trying to work, and I think it would if the camera were connected.


Here's the first part of the script:

```
#!/bin/bash
echo clear
/home/chris/camera/sdk-1.2.2/bin/delete -p5 -s5 -a
echo take
/home/chris/camera/sdk-1.2.2/bin/snap -p5 -s5 -f3 -r1 -q1 -e2 -m2
echo dump
#/home/chris/camera/sdk-1.2.2/bin/dump -p5 -s5 -f1 

8< snipped the rest >8
```


Interestingly, the -a appears a different colour in the gedit window, and since the 'take' line seems to work I'm wondering if that -a is affecting the way the script runs rather than being sent to sdk along with the other parameters.

Without that -a on the end, delete returns the same message, due to the missing parameter.

```
chris@cginternet:~/camera$ /home/chris/camera/sdk-1.2.2/bin/delete -p5 -s5
Usage: delete [ -p port number (0-8) ] [-s baud rate (0-5) ] -n picture number
       delete [ -p port number (0-8) ] [-s baud rate (0-5) ] -a all
chris@cginternet:~/camera$

```

Any ideas how to get around it?

---

