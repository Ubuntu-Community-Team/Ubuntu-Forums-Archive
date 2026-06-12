---
title: "Installing applications, EG pidgin?"
date: 2008-06-11
forum: General Help
---

### Post by citricsquid on 2008-06-11
"The list of applications is not Availabe" (Typo is in the error message).
Then it has "Refresh" and "cancel".

I click "Refresh" and it says; "Downloading package information" Then it hangs for a few seconds and goes back to the old screen, this happens everytime i try and install it.

What's the problem? Same with every application, 4th I've installed ubuntu and I really hope this works :(

---

### Post by ibutho on 2008-06-11
Try doing it from the command line and take note of any errors printed on the screen. Try Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install pidgin

```
Replace pidgin in the above example with any app you wish to install.

---

### Post by citricsquid on 2008-06-11
It worked, perfectly.
Thankyou <3.

---

