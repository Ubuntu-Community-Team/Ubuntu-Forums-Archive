---
title: "[SOLVED] Monodevelop white fonts"
date: 2007-10-03
forum: General Help
---

### Post by Lord Illidan on 2007-10-03
I've got a really infuriating problem.

I am using Monodevelop 0.16 (not from Ubuntu repositories), and in the Edit->Preferences Dialog, options which are not checked are shown in white.

This clashes horribly with the light background of clearlooks and ubuntulooks. I also had this problem with Monodevelop 0.14..I am running gutsy. Can anyone help? I attached a screenshot.

---

### Post by Lord Illidan on 2007-10-03
Bump..anyone knows a trick or two? I tried changing themes, but it seems to be very persistent.

---

### Post by Lord Illidan on 2007-10-04
Bump...anyone?

---

### Post by Lord Illidan on 2007-10-08
Another bump! Am I the only one here?

---

### Post by lgespee on 2007-10-08
Maybe you are the one of the few that has MonoDevelop 1.0 beta (0.16) currently installed on Ubuntu. Did you compile it yourself or did you use a backport?
If you can tell me where you got it, I could try if I can duplicate your issue.

---

### Post by Lord Illidan on 2007-10-11
I solved it. But the solution is not very nice.

I like having transparent panels, however the default black text doesn't show on some wallpapers, so I use these settings in the gtkrc2.0 file :

```
style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
```Unfortunately, it seems that monodevelop was picking up this colour and using it..

EDIT :Yep, look at this. I am using a new gtkrc, btw..for those who want to look at it, I attached it here. Just save it as .gtkrc-2.0 if you want to look at it.

I think it's a bug on MonoDevelop's part. I see no reason why the text used there has to depend on the panel text colour.

---

### Post by Lord Illidan on 2007-10-11
I have reported a bug here, if anyone wishes to look at it : [https://bugzilla.novell.com/show_bug.cgi?id=333112](https://bugzilla.novell.com/show_bug.cgi?id=333112)

---

### Post by Lord Illidan on 2007-10-11
Not a bug, it seems.

So, the real problem lies with the damn gnome-panel!

---

### Post by Lord Illidan on 2007-10-12
Ok, solved it. For anyone who still has interest in this, the way to do it is by specifying the names of the widgets more closely in the gtkrc.
```

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*Panel*Clock*" style "my_color"
widget "*Panel*MenuBar*" style "my_color"
widget "*Panel*Task*" style "my_color"  
```This should be enough.

---

### Post by brk3 on 2007-12-28
Thanks for this, had the exact same problem!

---

