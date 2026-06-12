---
title: "Webcam not working on skype - ubuntu 12.04 32bits"
date: 2013-02-26
forum: General Help
---

### Post by Ingla on 2013-02-26
Hello.

I added this post in error to a closed post at [http://ubuntuforums.org/showthread.php?t=1984328&page=2](http://ubuntuforums.org/showthread.php?t=1984328&page=2). So, it probably was incomprehensible. The problem is the webcam is not working in Skype.

On that post papibe wrote:

> You need to set the variable LD_PRELOAD permanent in your environment. You have 2 options:

1. For personal use (just your user) add this line to your ~/.bashrc
Code:
export LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
2. For system-wide, add this line to your /etc/environment
Code:
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
Then restart your machine.

Then Apanta wrote:

> I created a new file on my desktop, named it Skype.
inside there are the lines you wrote. I saved file and closed it.

In properties/permission I signed it executable.

Now launching by double click on the file Skype works and the webcam runs ok.


[COLOR=#0000cd]**_To this, I wrote_**:[/COLOR]

I'm running 12.04 32-bit.

Have not been able to get the webcam working (when I go to video options in Skype, the camera is working but will not go on when I make a call).

I added the line to bashrc *AND* made the desktop file. The file opens Skype but still no cam. 

(There is a skype.desktop in /usr/share/applications, which is not the same as the one I made on the desktop)

Can someone please show me the complete and exact contents of a working skype.desktop file? Maybe I've copied something wrong.

Any help appreciated.

Thanks.

---

### Post by papibe on 2013-02-26
Moved to its own thread.

---

