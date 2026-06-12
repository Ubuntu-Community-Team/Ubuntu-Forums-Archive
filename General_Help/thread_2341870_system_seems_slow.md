---
title: "system seems slow"
date: 2016-11-01
forum: General Help
---

### Post by jgw on 2016-11-01
This is about an eee pc 1005hab.  This machine is a little laptop and doesn't get a lot of use unless traveling.  Its my wife's travel machine.  Details:
Memory    991.7Mib
Processor  intel atom cpu n270@1.60GHzX2
Graphics   intel 945GME x86/MMX/SSE2
OS type    32-bit

Yesterday I was trying to open and install a program but could never get the software center to completely open.  I started rooting around trying to figure out what was going on.   I do have the multiload indicator running and it shows me that the load color is solid although the load itself is only at 2.41 (was over 5.??) but the cpu use is at 92% The network is doing little or nothing so, I think, this would mean that something is using a LOT of system resources. When I look at the system monitor it tells me that the software-center is using 43% of the cpu, compiz 18, and about 4 other things runnning 2 to 1% of the cpu thing. I am, obviously, confused and ignorant on this stuff. All I really know is that this machine seems to be doing much but I can do just about nothing. The only programs actually running is the system monitor and the sofware center.  I have also noticed that when I try and check stuff I eventually get a notice that a script is messed up.  I normally just close those and it seems to make no difference.  

I realize that this machine isn't exactly the swiftest on block but just stopping is a bit offputting.  My suspicion is that I may be trying to do too many things with it and its just not up to it.  My suspicion is that if the load completely fills its box, in the indicator the wise thing would be to simply stop and wait until the load goes down instead of foraging ahead and giving the machine more work when its already pretty much at its limit.  On the other hand somebody may have a whiz bang idea about speeding things up <G>

I am writing this to see if there is any agreement on my thoughts about this.  (am I right about just slowing down and, when its showing a load - wait)

Thank you...................

---

### Post by T.J. on 2016-11-01
> **jgw said:**
> 


I realize that this machine isn't exactly the swiftest on block but just stopping is a bit offputting.  My suspicion is that I may be trying to do too many things with it and its just not up to it.  My suspicion is that if the load completely fills its box, in the indicator the wise thing would be to simply stop and wait until the load goes down instead of foraging ahead and giving the machine more work when its already pretty much at its limit.  On the other hand somebody may have a whiz bang idea about speeding things up <G>

I am writing this to see if there is any agreement on my thoughts about this.  (am I right about just slowing down and, when its showing a load - wait)

Thank you...................

If I may make a humble suggestion?  Software Centre is not a bad piece of software, but it IS slow in my experience - even on high end machines.  Please try Synaptic in its place.  It's a bit more daunting - and a bit more techie - but it should work better, especially on slow machines.  Once you get used to it - it works very well.

You can install it in a terminal using:

sudo apt-get install synaptic

If you don't like it, you can still use Software Centre.  They can co-exist quite happily, but you can only use one at a time - because only one program is allowed to install packages at any one time to keep from breaking things.

---

### Post by jgw on 2016-11-01
Thank you for the reply.

I use synaptic.  My experience with the software center was an example.  The entire machine gets stuck and displays the load.  When the load becomes full I think I should just wait but am not sure.  I think that the problem of slow is intrinsic to the machine in question and so the user should check the indicator and when it shows the machine is getting swamped one should use common sense and just wait for it to finish the current tasks.  

On reflection I think I have answered my own question.  Just had to work through it.  If the machine is a dog don't blame the operating system.  I think I need validation but I am over that one too.  

Thanks for the help! (made me think it through)

---

### Post by jerome1232 on 2016-11-01
A load over 2 for a 2 core machine is a swamped machine.

Unity is isn't the lightest desktop environment around. I would try a lighter interface like Ubuntu Mate, or Xubuntu, or Lubuntu. I've had success with Mate on a 1.2 ghz intel core 2 duo with 2 gb's of ram.

---

### Post by ajgreeny on 2016-11-01
I am almost surprised that you have managed to get Ubuntu with unity to run at an acceptable speed on that machine.

As compiz, which is essential to the running of unity is taking almost one fifth of resources, and software-centre is using almost half, it is definitely time to move to a much lighter package manager and DE, or even just a window manager instead of a full DE, though that may take more learning and getting used to.

It could be worth having a look at Bodhi which is based on Ubuntu, uses its repos and therefore a lot of its packages, but is very much faster as it uses the Enlightenment DE, very attractive to look at, but does things a bit differently so also takes a while to get to know. Have a look at the website at [http://www.bodhilinux.com/](http://www.bodhilinux.com/)

If you really want to stay within the *ubuntu family proper I would also suggest Lubuntu 16.04.1, but if you do decide to try that, you will need to be aware of the bug that gives you a black screen and no GUI, easily overcome as shown in my post 13 of the bug thread at [https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460)

---

### Post by jgw on 2016-11-03
wow!  Thanks for the replies!

Looks as if I have to change the interface and I will study on that one - thanks again! (I should have figured that one out)

---

