---
title: "Random Text Subsititutions in HTML-Rendered Text"
date: 2015-01-03
forum: General Help
---

### Post by buzzingrobot on 2015-01-03
Has anyone else come across this little annoyance:

I'm seeing incorrect text characters here with HTML-rendered text:  In Firefox (34.0), Liferea, etc., individual characters are often replaced by another, incorrect character. For example, an upper-case 'A' may be replaced by an upper-case 'H'.  

Text is not distorted, just replaced.

These substitutions are temporary, in that they seem to disappear when the page is redrawn. Also, only a single character is affected at any time, but every single instance of that character will be affected.  E.g., if the 'A' is replaced by the 'H', then *all* A's are replaced by H's, while all other characters display correctly. There's no apparent pattern or consistency about what characters are replaced, or when.

Text that displayed correctly may become incorrect after switching away to another workspace and then switching back.

While a page redraw seems to fix one substitution, it often brings about a new substitution.

Toggling 'Hardware Acceleration' or 'Smooth Scrolling' in Firefox have no impact.  It affects installed fonts as well as fonts downloaded by a page.

Google isn't helping much, so far.

(Stock Unity 14.10 except for CCSM installed and Viewport Switch with scroll wheel enabled; Ambiance theme with out-of-box fonts; Radeon 8570 on the default open video stack.)

---

### Post by TheFu on 2015-01-03
Me too, for the last 2 months or so.

I'm seeing multiple changes in Firefox inputs for unknown reasons. Only with text that I enter .... like userids and passwords. ;( Doesn't matter if I type it or use KeePassX autocomplete, the text is wrong.  After a reboot, it seems to be fixed for a few days.  It only happens on this single machine 14.04 x32 - a C720.  Other machines running the same 14.04 and x32 don't show this issue.

I think it is a wild pointer issue somewhere in the input code .... it works fine in a pure xterm and many other applications.  Really only notice the issue in Firefox v34.0 ... 

Also, I don't touch non-LTS releases.

---

### Post by vasa1 on 2015-01-03
Does the problem occur when typing in the "reply" area at ubuntu forums?

---

### Post by TheFu on 2015-01-03
> **vasa1 said:**
> Does the problem occur when typing in the "reply" area at ubuntu forums?

Not today, but previously - yes.  Appeared to happen in any input field inside firefox. 
Another, possibly related (but I'm not certain), is that keepassx autocomplete doesn't work on this system, but does on the others. Haven't a clue why.  This machine is full disk encrypted. That's the only thing I can think of as different - well - and the desktop is running directly on hardware. On the other machine without any issues, the desktop runs inside a KVM virtual machine accessed through x2go.

---

### Post by buzzingrobot on 2015-01-03
I see it only in HTML-rendered text that's styled with CSS.  I haven't seen it elsewhere. Or here in the entry box.

Going to switch to Intel video for a day and see what happens.

---

