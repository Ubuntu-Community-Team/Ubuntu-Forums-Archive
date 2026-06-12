---
title: "How should samba work on edgy"
date: 2006-11-12
forum: General Help
---

### Post by wilko10 on 2006-11-12
How should samba work on edgy? I have setup samba serving before back in the days of Hoary I think and it seemed easier. I'm also stuck as well!!

I used the GUI system-->administration-->shared Folders and it installed some stuff and I set us a share and made read/write with the tick box (samba.conf confirms the writable=yes bit).

However it was not seen by my windows PC (it did with hoary/dapper) permissions it seems . I had to follow this page:- [https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)

specifically this bit :-
sudo  smbpasswd -a remoteuser
and I setup a new user on edgy called remoteuser

Now it works but read only BUT the samba.conf file definatly has writable=yes and the GUI bit above confirms this.

a) what do i need to do to get my edgy samba share writable
b) Is this as good as it gets? I had my hopes raised by the GUI program but it seems it's only done half a job. Cannot the remainder of the process be done by default using the GUI?

thanks

Jeff

---

### Post by wpshooter on 2006-11-12
Dear Wilko:

I hope I am wrong, but yes I think this is as good as it gets, at least for now.  I tried to get sharing going on a couple of Edgy machines that I installed and it worked on an inconsistent basis at best.

I just can not understand how they can be working on all kind of other stuff in these O/Ss and just ignore something as fundimental as folder/file and printer sharing which can be accomplished on a Microsoft windows network with just a few simple clicks in a GUI which has been doable for probably over 15 years now.

They are probably loosing a lot of users by ignoring fixing these functions.

---

### Post by Subnet on 2006-11-12
Samba works great for me on edgy, but I configured mine by hand. There is an awesome GUI tool that I have used before, it's called gsambad. Hope that helps.:)

---

### Post by podunk on 2006-11-12
Setting up a network between Linux machines is a point and click thing that takes just a few minutes. It's when you try to hook Windows and Linux together that you have the problem - and the problem isn't the Linux machines reading the widows network (that's easy), but rather vice versa.

If Microsoft would follow the standards of the rest of the computer world it would be not only easy to set up the network, but much more secure also.

I did this in dapper:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

Took about 10 minutes per machine on Linux, the Windows set up took a bit longer due to the reboots.

---

### Post by jethro10 on 2006-11-13
Ok,

thanks for that, i'll look at the GUI gsambad

Jeff

PS: OOPS! I asked the question in error with my Wife's account, hope she forgives me.

J

---

