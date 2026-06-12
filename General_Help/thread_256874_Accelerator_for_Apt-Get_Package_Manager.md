---
title: "Accelerator for Apt-Get Package Manager"
date: 2006-09-13
forum: General Help
---

### Post by muffinhead on 2006-09-13
Hi all, I know usually the use of Accelerators, or download Accelerators is not looked upon too greatly by websites.

The problem is, I don't have much of a choice. I am on 56k Dial-Up where I live, and broadband is not available in my area at all, it's like living in the boondox :lol:

So I need a download accelerator for Linux, mainly the Apt-get Package manager, that lets me pause and resume my download, so incase I get disconnected I can alway's resume it later, and my whole download is not lost.


The reason is, that I want to download and Install XGL, and some other packages, and they are too big for me to download without some kind of pausing/resuming method.

I have heard of axel, but I don't think it works with the Apt-Get Package manager, and am not sure if it features the pausing or resuming of a download.

Can anyone help or tell me if there is a way to do this, or even a accelerator for the apt-get package manager?

Thank You:)

---

### Post by pravuil on 2006-09-13
The weird thing about apt-get is that when you download the packages you don't need to download them again. The packages remain in the cache even if the process ends. Just cancel the download when you need to and start the process again at a later time.

There are download managers for Linux [http://en.wikipedia.org/wiki/Comparison_of_download_managers](http://en.wikipedia.org/wiki/Comparison_of_download_managers) Haven't tried them out myself but this should help you out. My suggestion for updates. Download the small packages through synaptic and then go to [http://packages.ubuntu.com](http://packages.ubuntu.com) to download the larger packages with the download manager. Hope that helps.

---

### Post by muffinhead on 2006-09-13
Thanks for your reply, but are XGL, and Compiz in the Synaptic package Manager? I believe it caches the packages fine in synaptic, but Xgl or Compiz is not available in Synaptic. Also Does the package remain if I turn off or restart my computer, when using synaptic?

So therefore I may need to use apt-get in the terminal to install xgl, compiz, and thier dependencies/Libraries, and I don't believe that I can cache packages by using apt-get in the terminal.

I was hoping there may have been some addon/frontend that would let me do this, but it seems there isn't.

I apologise if my post is incoherrent, as I'm really tired atm, and don't mean to sound like a n00b;)

---

### Post by bikeboy on 2006-09-13
Synaptic is simply a front end to apt-get, anything you can get via apt-get you can get through Synaptic. It's all about the repositories, you probably need Universe and/or Multiverse enabled.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by muffinhead on 2006-09-13
Thanks, I didn't realise all this before. I just started using Linux about four or five months ago, but am picking up fairly quickly on it. I apoligise if my question sounded a bit noobish.

Btw does a free web accelerator (Not Download Accelerator) Exist for Linux, that can accelerate the speed and loading times of webpages?

I came across toonel, but m not sure how to use it. If there is any out there please let me know, thank you:)

---

### Post by bikeboy on 2006-09-14
Being a noob isn't a crime :)
Not sure about the accelerators, but maybe one of the web browsers allows pre-fetching, which is essentially the same thing.

Have a look for the features of Epiphany, Galeon, Opera, Konqueror (all the browsers I can think of) to see if any of them have it.

---

### Post by ciscosurfer on 2006-09-14
You can enable prefetching (if it's not already on by default) in Firefox...

Doing so, however, will have zero effect on your download speeds for a specific file; it makes it so getting to a site is quicker because it's already located in your cache from a previous session.  If prefecting was the same as download accelerators, then download accelerators wouldn't exist.  Download accelerators grab multiple segments of a file and them piece them together.  

Muffinhead, if you are still interested, I would recommend you look at the link in pravuil's post.  But as far as I know, there are no da's for apt (you can always go to packages.ubuntu.com, though, after you get an accelerator, and then download packages via a browser and your new da).

---

### Post by kuja on 2006-09-14
In my experience with dial-up Opera was my savior. You can set it so it can download things once, and they remain in the cache forever if you want, for say, images, and it also has a separate setting for the same with documents. I set it to check the documents every five minutes, and images and other media never. Extremely Convenient.  

Apt-get should auto-resume downloads - should anyway. There is a "partial" folder within /var/cache/apt/archives for partially downloaded files, so resuming should work. 

I'd recommend using a download manager with your browser so you can resume broken downloads as well. If you use kubuntu, kget works nice. If you use ubuntu, take a look around, there around for it too.

---

### Post by muffinhead on 2006-09-14
Thank you for your replies, I really appreciate it, although I got back a little too late with a response, I just wanted to thank you all for your help.

The problem I'll probably have with xgl, Is finding and downloading all the required dependencies, and libraries to get it to work.

Thank you very much:wink:

---

