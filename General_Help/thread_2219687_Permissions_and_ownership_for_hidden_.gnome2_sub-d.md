---
title: "Permissions and ownership for hidden .gnome2 sub-directory"
date: 2014-04-25
forum: General Help
---

### Post by Edward_Diener on 2014-04-25
I am running Unity under the latest Ubuntu 14. Under my home directory there are a number of hidden subdirectories. A few of them have the 'owner' and 'group' as 'root' with no 'other' access of any kind. One of these is which is set in this way is .gnome2 ( the other is .dbus AFAICS ).

Since I am running Unity under Ubuntu 14, and it is based on Gnome3 as I understand it, why would I have a .gnome2 subdirectory ?

I did try an install of Nemo, to replace Nautilus. Might that be the reason why I have a .gnome2 sub-directory ?

Is the .gnome2 subdirectory supposed to be locked against my access as a user ? Because I discovered when I started Firefox or Thunderbird that both failed because they could not write to the .gnome2 subdirectory. I succeeded by making my own group the group owner of the .gnome2 subdirectory instead of the 'root' group. But why would Firefox or Thunderbird be writing files within this subdirectory ?

In other words something happened whereby Firefox and Thunderbird needed to write files to this subdirectory but I as a user was locked out of it, so naturally Firefox and Thunderbird failed to start. Although I have manually corrected it I would like to understand how this happened on my system.

---

### Post by deadflowr on 2014-04-25
I don't know what you might have done, but I have nothing in my home folder owned by root, except for those files which I had moved/copied using sudo, for some reason.

You probably want to change the ownership back to you.

---

### Post by Edward_Diener on 2014-04-25
> **deadflowr said:**
> I don't know what you might have done, but I have nothing in my home folder owned by root, except for those files which I had moved/copied using sudo, for some reason.

You probably want to change the ownership back to you.

I did change any subdirectory of my home directory, which was owned by 'root' and/or by the 'root' group, to my own signon and group. Among the others I found which were owned by 'root' were the .dbus and .gvfs subdirectories. I know I never directly created or changed either before so some software which was installed erroneously set the incorrect owner and group for both.

---

