---
title: "Is Ubuntu 16.04 ready to work with nvidia optimus card - continous problems"
date: 2016-10-02
forum: General Help
---

### Post by Pitero on 2016-10-02
[FONT=arial]Hi,

I have Ubuntu 15.10 with kernel 4.2.0-38-generic with [/FONT]352.63 nvidia propietary driver. Generally it works fine but I have problems with displaying the screen on two different monitors connected (one laptop internal, one external hdmi) with two different resolutions and frequency rates (60Hz, 50 Hz - not sure why here system try to run 50 Hz only while monitor is capable 75Hz according to specification).

I've tried few times to upgrade to 16.04. First to 16.04, next to 16.04.01. In both situations I've failed due to terrible problems with nvidia optimus drivers. In the first case it seemed it's was only problem with drivers, in the second case when installing ubuntu I've received first thousands of messages about problems with packages (could not install (and here package name) , unable to open (name), operation not permitted). After restarting it was total nightmare.

Now the questions:
- Why there are so terrible problems with new version of ubuntu and nvidia optimus card?
- Is there any way to install 16.04 in quick and stable way (as I'm tired because of spending many hours on fighting)? Has anyone installed this successfully?
- And finally why Canonical doesn't test the new releases better?

Regards

---

### Post by Pitero on 2016-10-05
I've just checked with one internal monitor and one connected via displayPort. I have the same problems. Any help?

---

### Post by monkeybrain20122 on 2016-10-05
I never have an Optimus laptop but my understanding is that official Linux support for optimus is kind of sketchy (for a few years there was no official support at all), there is a community solution called bumblebee, I heard it is very good but then I have no experience in Optimus.

Here is a reasonably recent survey [http://www.thelinuxrain.com/articles/the-state-of-nvidia-optimus-on-linux](http://www.thelinuxrain.com/articles/the-state-of-nvidia-optimus-on-linux)

---

### Post by Pitero on 2016-10-11
I have impression that it's rather some incompatibility of kernel and nvidia drivers....

---

