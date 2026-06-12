---
title: "How do I add a bug report and make sure it is assoc with the right project?"
date: 2008-04-02
forum: General Help
---

### Post by MountainX on 2008-04-02
Launchpad is frustrating. I do not think it is very user-friendly or well-designed, but that isn't the point of this post. I have decided to make the effort to figure it out so I can properly report bugs. I would appreciate some help.

Here is today's specific problem with reporting bugs.

1. Nautilus exhibits bug but produces no error. I decide to take a screen shot.
2. It turns out I cannot find a way to capture a screen region so I have to capture my whole desktop dual monitor 1920 x 1200 and then edit in GIMP. That's a bit of a pain (compared to the functionality I'm used to in Windows), but I get it done. (And no, capturing a single window wasn't satisfactory as you will see if you look at my screen shot.)
3. I go to Launchpad and have to go through several clicks before I can even start to report a bug.
4. When I try to specify the project = Nautilus in Launchpad, I get this error "There is no project named 'nautlius' registered in Launchpad"
5. Of course Launchpad loses the information I have specified about attaching my screen shot, so I have to go through those steps again (ultimately I had to do that 3 times).
6. Finally I complete my bug report
7. Next I attempt one more time to associate my bug with some projects but I am pretty sure I'm doing it wrong because it tells me nautilus isn't managed by Launchpad. 

Here's the bug report.
[https://bugs.launchpad.net/gvfs/+bug/210881](https://bugs.launchpad.net/gvfs/+bug/210881)

I feel like I wasted my time because no one will ever see this bug report.

---

### Post by kostkon on 2008-04-02
> **MountainX said:**
> Launchpad is frustrating. I do not think it is very user-friendly or well-designed, but that isn't the point of this post. I have decided to make the effort to figure it out so I can properly report bugs. I would appreciate some help.

Here is today's specific problem with reporting bugs.

1. Nautilus exhibits bug but produces no error. I decide to take a screen shot.
2. It turns out I cannot find a way to capture a screen region so I have to capture my whole desktop dual monitor 1920 x 1200 and then edit in GIMP. That's a bit of a pain (compared to the functionality I'm used to in Windows), but I get it done. (And no, capturing a single window wasn't satisfactory as you will see if you look at my screen shot.)
OK, fair enough about this.
> **MountainX said:**
> 3. I go to Launchpad and have to go through several clicks before I can even start to report a bug.
4. When I try to specify the project = Nautilus in Launchpad, I get this error "There is no project named 'nautlius' registered in Launchpad"
I don't see where's the problem. When you go to report a bug, you can easily search for the package or project you want by selecting *Choose...*
> **MountainX said:**
> 5. Of course Launchpad loses the information I have specified about attaching my screen shot, so I have to go through those steps again (ultimately I had to do that 3 times).
I don't actually understand what happened here.
> **MountainX said:**
> 7. Next I attempt one more time to associate my bug with some projects but I am pretty sure I'm doing it wrong because it tells me nautilus isn't managed by Launchpad. 

Here's the bug report.
[https://bugs.launchpad.net/gvfs/+bug/210881](https://bugs.launchpad.net/gvfs/+bug/210881)
This is a thing that a bug triager does and not the bug reporter. The status, importance and assignment are set by a bug triager.
> **MountainX said:**
> I feel like I wasted my time because no one will ever see this bug report.
Why do you say this??! Nevertheless, if you would like to help with bug triaging, you could join the [*BugSquad team*]("https://wiki.ubuntu.com/BugSquad").

---

### Post by wolfen69 on 2008-04-02
> 2. It turns out I cannot find a way to capture a screen region
alt-prtsc will capture only active window.

---

### Post by MountainX on 2008-04-02
I have thought about joining the 5-a-day as an end-user, but first I would like to get my own system functional. Right now, almost nothing works. I can't even accomplish basic tasks, so it makes it hard to contribute to anything, much less get any work done.

And as far as reporting bugs, your replies didn't help me understand what is going wrong. You said:

"I don't see where's the problem. When you go to report a bug, you can easily search for the package or project you want by selecting Choose..."

I said that the result of doing that was this:
**[COLOR="Red"]"There is no project named 'nautlius' registered in Launchpad"[/COLOR]**

This happens to me every single time.

I'll ask a few more specific questions:
1. what is the difference between a package and a project at this Lauchpad screen? (I tried choosing nautilus for both and I got an error in each one.)

2. How do I know what to enter in package or project (once I understand question 1 above)?

3. What happens if I leave these fields blank? Is my bug report ignored or delayed?

---

### Post by MountainX on 2008-04-02
> **wolfen69 said:**
> alt-prtsc will capture only active window.

Is there an easy way to capture a region?

---

