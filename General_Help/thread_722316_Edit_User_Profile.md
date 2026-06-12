---
title: "Edit User Profile"
date: 2008-03-12
forum: General Help
---

### Post by steve keating on 2008-03-12
I am trying to create a user profile template to be used by select users. I have used the User Profile Editor GUI, but once I save the changes, they do not stick. When I go back in and Edit the profile I can see all of the changes I first made have been reset to default. When I log in as a user using the profile template, the changes made are not there. How can I create a user profile template, either using the User Profile Editor GUI, or which file must be edited? For the GUI, what are the steps to make the changes permanent?

---

### Post by Apfelmaennchen on 2008-03-15
Hi,

I'm not quite sure what you mean EXACTLY. If the only things you want to customize are
*the set of groups
*login shell
*home-prefix
*uid-range

you might want to take a look at /etc/gnome-system-tools/users/profiles

Maybe it's even possible to setup additional information using this file.
However I'm still searching for that information - that's how I came across this thread.

HTH
A

---

