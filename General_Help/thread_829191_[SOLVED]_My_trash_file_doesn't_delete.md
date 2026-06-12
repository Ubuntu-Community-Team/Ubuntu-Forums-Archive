---
title: "[SOLVED] My trash file doesn't delete???"
date: 2008-06-14
forum: General Help
---

### Post by L337_K3y5 on 2008-06-14
[LEFT]This is my problem...The mod that I used to patch my Wireless adapter to get online, is in the trash, but when I try to delete it, it brings up an error message like this:
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Undeleted_Trash.png[/IMG]
The weird thing though is that its empty and brings up this message:confused:.  I don't know what to do to delete it for good.  Also, it says PERMISSION DENIED.  I don't know if I'm supposed to get rid of it...I think I have a copy of it in my home directory, so getting rid of it shouldn't pose a threat to my wireless. [/LEFT]

---

### Post by spiderbatdad on 2008-06-14
try chowning the file:```
sudo chown L337_k3yz:L337_k3yz ~/.local/share/Trash/madwifi
```note the T in Trash. You should then be able to empty it from trash. Of course L337_k3yz would be replaced with the actual login name you use, if it is different.

---

### Post by L337_K3y5 on 2008-06-14
This is what I get whenever I try to do the Chown:
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Screenshot-andrewandrew-laptop.png[/IMG]
What's up with that?:confused:

---

### Post by drs305 on 2008-06-14
You can just chown your entire home folder, which should belong to you anyway:

```

sudo chown -R username:username /home/username

```

Then empty the trash.

---

### Post by L337_K3y5 on 2008-06-14
Solved!!!

---

### Post by heatpumpcontrol on 2008-06-14
login in as root

```
gksudo nautilus
```

go into /media/home/<username>/ and look for your trash. Oh, be sure to hit cnt+H to show hidden files

Now right click on the file to delete and properties->permissions

select yourself as the owner and make sure you assing read/write permissions too.

now open or go back to the preview nautilus window and into your trash and delete the file.


Note: Mark Thread as solved to help others.

---

### Post by spiderbatdad on 2008-06-14
> **L337_K3y5 said:**
> This is what I get whenever I try to do the Chown:
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Screenshot-andrewandrew-laptop.png[/IMG]
What's up with that?:confused:

I think the system no longer recognizes the filename, once it has been moved to Trash, so my suggestion was impossible.:oops:

---

### Post by drs305 on 2008-06-14
> **spiderbatdad said:**
> I think the system no longer recognizes the filename, once it has been moved to Trash, so my suggestion was impossible.:oops:

It was just one folder short:
```
sudo chown L337_k3yz:L337_k3yz ~/.local/share/Trash/madwifi
```
It ends up in ~/.local/share/Trash/**files**/madwifi and it probably needs the -R switch, if madwifi is a folder

---

### Post by Bob Allen on 2008-06-16
Using chown for the entire /home folder worked for me! I tried changing the permissions and everything I could find in the other posts and nothing seemed to work. I am using Kubuntu Gutsy. Thanks for this post.

---

