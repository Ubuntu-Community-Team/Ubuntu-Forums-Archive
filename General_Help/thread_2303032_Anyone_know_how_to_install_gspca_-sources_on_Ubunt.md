---
title: "Anyone know how to install gspca -sources on Ubuntu 10.04 64-bit ?."
date: 2015-11-15
forum: General Help
---

### Post by Ricardo_Velasco on 2015-11-15
Cheers:

In these last days, I switch to the previous version of the previous Ubuntu 10.04 LTS is ..

Then to install my camera Genius Eye 312 look in forums without any problems but after a while I get install having wrong architecture as the 32-bit ..

After that I've been trying to look for 64-bit package and install not make it ..

Use all kinds of methods .. one of them it was using force package architecture .. but all I got was nothing ...

So I need your help with this problem ..

Thank you

Update:

This solution is for the driver of Eye 312 camera or other cameras compatible with the operating system appears ..

To see if it supports UVC download .. If you exit the picture is that the driver has a computer but has to be installed by a package 
To view the image in Skype on Ubuntu 12.04 LTS 64 - bit

---

### Post by Vladlenin5000 on 2015-11-15
Hi and welcome.

Ubuntu 10.04 is EoL. No further support. Please install a supported release. Same answer as the one in Ask Ubuntu: [http://askubuntu.com/questions/696547/is-there-any-gspca-sources-package-for-ubuntu-10-04-64bit](http://askubuntu.com/questions/696547/is-there-any-gspca-sources-package-for-ubuntu-10-04-64bit)

PS - Webcams are plug&play (most of them). Why are you looking for outdated software that simply doesn't work now?

---

### Post by Ricardo_Velasco on 2015-11-15
Cheers:

I answer your question , first I want to ask a question ?

I need support forums with current LTS versions of Ubuntu? .. If I have one of those do not give me support anywhere?

That's my first question.

I tell you .. crossed my head this idea of installing a driver WebCam as said in the post called Genius Eye 312 ..

He had the version 13.04 of Ubuntu and try to download gspca -sources but not served me the end of it then try to find the solution in another earlier version of Ubuntu and even more do not find ..

So I put this post and AskUbuntu aver if I could help with this incognita but never mind ..

Also I do not upgrade to newer as 14.04 or 15 because these versions are not as stable and prefer a more safe to use, because I experiment with Ubuntu ..

So one more question ? .. Here I have to add ( Fixed ) in the title of the post ... ?

Thank you

---

### Post by Vladlenin5000 on 2015-11-15
1. Your English is (almost) gibberish (if you're Spanish then it's hardly surprising). That fact alone suggests you would be better served by an Ubuntu forum in your own language (also suggested at Ask Ubuntu).

2. The currently supported Ubuntu releases are 12.04 (LTS - until April 2017), 14.04 (LTS - until April 2019) and 15.10 (non-LTS - 9 months support only). 15.04 still has a couple of months left.
For obvious reasons, unsupported releases SHOULDN'T be used.

3. Your reasoning (or lack of it) is atrociously flawed and factually wrong. You don't know what you're doing and you learned nothing since this interesting (and quite revealing) dialogue: [http://www.ubuntu-es.org/comment/514985#comment-514985](http://www.ubuntu-es.org/comment/514985#comment-514985).

4. Genius Eye 312 should be natively supported by now - there are NO POSTS anywhere in the webs of people complaining about that webcam newer than 2009 - and if not, it never will. Buy another one, problem solved. The cheapest you can find nowadays is certainly supported (as in "plug&play") and overall better than that Genius garbage.

---

### Post by Ricardo_Velasco on 2015-11-15
Cheers:

Sorry for the ignorance ..

But recently I am learning and trying to learn on this operating system ..

And a question to you ? .. You think I was speaking in a tone of disrespect? ,,, I do not want to deviate from the main theme but of no use in face show what I was before ...

If you want more information on the time I was about 13 years older .. One is immature and if I recognize that was an immature adult in a forum ..

I admit ..

My argument is not that it is illogical .. But for that very reason I'm asking you who knows more and more ..

I beg you to forgive me for my English and my conversation 2 years ago .. but neither side kick me in my mistakes ..

I ask immense excuse my English .. and my old conversation ..

Do not think I 'm in a tone of sarcasm , I'm talking seriously ..

Thank you very much and sorry

Please close the topic

---

### Post by Vladlenin5000 on 2015-11-15
I'm sorry too for not realizing you were so young... And from Ecuador, no less... However, age is no excuse for NOT asking the right questions and insisting (2 years in row?!?) in asking something unsolvable: The file you're looking for no longer exists but if it did it wouldn't work anyway. Do NOT look for solutions in old threads/posts/blogs. In the Linux world, 3 years ago was prehistoric times...

Again, your Genius webcam should be natively supported by now in any of the aforementioned supported releases, including 12.04 LTS. You may need to install *video4linux* and/or UVC.
Again, a new, better and completely supported webcam costs $5 or less (Amazon, eBay, DX, etc.).

---

### Post by Ricardo_Velasco on 2015-11-15
Please I beg A huge apology for silly questions I've done my part ..

Please forgive me .. and try to follow the rules of Linux and the forum

Thank you

---

### Post by Vladlenin5000 on 2015-11-15
Don't worry about that... ;-)

First and foremost, make sure the webcam is in working condition.
Just try a supported release and plug the webcam. If it doesn't work right away then install what I mentioned in the previous post (both available in Ubuntu Software Center), reboot. Still not working? You can try opening a new thread (@Hardware), correctly identifying your camera along with the results of *lsusb* and the Ubuntu version as well (any of the supported releases and no other) and also what you did already... But don't keep your hopes high. There's no point in troubleshooting obsolete hardware when there are plenty of choices.

---

### Post by Ricardo_Velasco on 2015-11-16
Solution for Ubuntu 12.04 LTS 


You are a genious
A big genius¡

Thanks for opening my head of what I had closed ...

Your recommendations too and helped me solve this big problem that I have ..

You were right .. to download UVC detect whether the camera and the image appeared but here comes the crossing ..

I'll tell you the steps you use to solve my problem and that other users can see it and put your camera ...

Veras first enter this page:

[http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html](http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html)

Here the main problem of the camera that appears in Black or Verlde exposed ...

Here it shows me a package essential for this type of cameras that can be placed on skype .. This package is called liv4l0 ...

It appears in the comments that the solution helped them .. but instead served me my no command that was appeared the following:


ricardo-root @ desktop: / usr / local / bin # LD_PRELOAD = / usr / lib64 / x86_64-linux-gnu / libv4l / skype v4l2convert.so
ERROR: ld.so: object '/usr/lib64/x86_64-linux-gnu/libv4l/v4l2convert.so' from LD_PRELOAD can not be preloaded: ignored.

As you see here .. change the file location .. because as we know the OS is 64-bit file showing me there is 32 bits..¡¡

But it appeared to me that there might be preloaded and soon want to enter skype not served me ..

Well before any confusion that this command is executed without terminal put:

sudo gedit /usr/share/applications/skype.desktop

And a line appears Exec =

In this line we put the above to load the file command .. or not you call it ..

But here's the complete solution:

[http://forum.ubuntu-it.org/viewtopic.php?f=95&t=546530](http://forum.ubuntu-it.org/viewtopic.php?f=95&t=546530)

This is a forum which appeared in another forum that is:

[http://ubuntuforums.org/archive/index.php/t-1937857.html](http://ubuntuforums.org/archive/index.php/t-1937857.html)

That would be the complete solution of the problem for installation on Ubuntu 12.04 LTS ..

Thanks for your recommendations, I could not figure this out three years ago .. But it works the camera on skype ..

Sorry for not being as detailed in my problem ..

Thank you thank you very much

---

### Post by Vladlenin5000 on 2015-11-16
I'm glad you found a solution.
Please use the thread tools to mark this one as solved.

---

