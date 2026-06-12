---
title: "Ubuntu 18.04 Firefox 68"
date: 2019-07-16
forum: General Help
---

### Post by OBI_Ron on 2019-07-16
Hello Everyone,

I asked this on Firefox support forum as well.  For the past week, I have been unable to manually type in my password for any login screen.  The password field is flashing when the cursor is in it, an it seems to take only 1 character - continuously overwriting the last character.  I end up having to type my password into a text editor, then copying and pasting.

Has anyone else seen this?

---

### Post by PaulW2U on 2019-07-16
No problems here but take a look at this bug report:

[Ubuntu 18.04's ibus package breaks password fields in Firefox again]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1836659")

Is that what you're seeing?

---

### Post by OBI_Ron on 2019-07-16
Hi PaulW2U - yes indeed, that is what I am seeing.  Any workarounds?

---

### Post by lisati on 2019-07-16
I suggest that you indicate on the bug report that it affects you too. 

Sorry, I don't have a workaround.

---

### Post by cruzer001 on 2019-07-16
Running 18.04 and FFesr without this bug.  So you may want to give it a try as a work-a-round.  Current ESR is FF60.

---

### Post by PaulW2U on 2019-07-17
> **OBI_Ron said:**
> Any workarounds?
I don't know how far you went into the bug report but one of the linked reports suggested copying and pasting usernames and passwords from another application. 

Maybe type into gedit and paste into Firefox with Ctrl-V. Does that work?

---

### Post by OBI_Ron on 2019-07-18
lisati - Done!

PaulW2U - Yes, that is what I have been doing - thanks!

---

### Post by OBI_Ron on 2019-07-18
So, I decided to try something else - I typically use Gnome fallback - When I log in using standard Ubuntu, I do not get the error - password fields behave as expected.

Is this a Gnome issue then?

---

### Post by PaulW2U on 2019-07-18
> **OBI_Ron said:**
> Is this a Gnome issue then?
Possibly. 

When Firefox previously suffered from this problem ([bug #1765304]("https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1765304")) the fix was applied to GNOME Shell.

---

### Post by walts48 on 2019-07-19
> **OBI_Ron said:**
> Hi PaulW2U - yes indeed, that is what I am seeing.  Any workarounds?

Install Firefox from Mozilla and forget about distro builds.

[https://www.mozilla.org/en-US/firefox/all/](https://www.mozilla.org/en-US/firefox/all/)

---

### Post by PaulW2U on 2019-07-19
Confirmation that the bug is in GNOME Flashback and not Firefox:

[Focusing on password field in Firefox causes ibus indicator to flicker]("https://gitlab.gnome.org/GNOME/gnome-flashback/issues/16")

---

