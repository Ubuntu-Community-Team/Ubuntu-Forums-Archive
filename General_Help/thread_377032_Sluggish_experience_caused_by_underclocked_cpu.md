---
title: "Sluggish experience caused by underclocked cpu?"
date: 2007-03-05
forum: General Help
---

### Post by obrie on 2007-03-05
Hi,

During the end of January, I made the move from Windows XP to Ubuntu Edgy Eft since I finally had the chance to.  I've enjoyed everything so far, but there's one major problem that may cause me to revert back to Windows.  Everything in Ubuntu is noticeably slower than Windows.  This includes video playback, web browsing, and just your everyday run-of-the-mill tasks that you perform on your computer.

These are the specs of the computer:

* 768MB RAM
* AMD Athlon XP 2100+
* 120GB HD
* Asus A7V333 Motherboard
* XFX GeForce 6600

I've installed the latest nvidia drivers and have dual-screen enabled.  I've disabled all services and applications that are unnecessary and even disabled many of the graphics features (such as showing contents of windows while dragging).  I've gone through many different optimization tutorials and nothing seems to help.

My only guess for this problem is that it has something to do with the fact that I'm underclocking my CPU.  The reason for underclocking it is that it is unstable at its normal CPU speeds (i.e. the computer crashes).  This was the case in both Windows and Ubuntu.  However, everything used to run very smoothly in Windows.

I'm fairly certain this is not a graphics driver issue since the nvidia drivers are enabled and being used.  I thought I could last another few months with the decrease in speed before I upgrade the computer, but it's become fairly frustrating.  I'm hoping that there's something I've missed in trying different things over the past month and change.  It simply doesn't sound right that a computer with the specs would run Ubuntu so slowly.  Am I mistaken?

Thanks for any help, I appreciate it.

---

### Post by markitect on 2007-03-05
A machine like that should run Ubuntu fine.  It might be useful to use the system monitor to watch your swap file.  If your using up all your memory and having to swap stuff out every time you run something it will make it run really slow, but i dont see that being a problem unless you you have open office running and firefox and opening another huge program (vmware maybe) and switching between them a lot.  hard drive crunching away when you alt-tab is a great example of this

Your processor should be a concern though.  I used to have a 2100+ and it got glitchy on me too.  I originally had it overclocked, so i set it to normal and it worked fine for a while, then i had to underclock it, then it started happening again.  I ended up getting a athlon xp 2500+ barton core and it works fantastic and runs cooler (note your board needs to support the 333 fsb for it) and it runs ubuntu great to this day, although im now counting the days till socket am2+ comes out second half of this year.

---

