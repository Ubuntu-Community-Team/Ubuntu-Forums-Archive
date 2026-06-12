---
title: "all my user groups are distroyed - please help!"
date: 2007-07-09
forum: General Help
---

### Post by mental_drummer on 2007-07-09
So in trying  to set up vmware to run my windoze partition from Ubuntu Edgy I attempted to add my user to group 'disk' using the command

sudo usermod -G disk niall

where niall is obviously my name.

So I think as a result I now cannot use sound, run admin applications like Synaptic and lots of other worrying stuff. I have found out from these forums that this is very bad and now i only seem to belong to groups 'niall' and 'disk'. However another user on my system still belongs to lots of groups but shows the same symptoms of no sound etc. The other post on the forums says that there is no solution and I must reinstall linux but i really dont want to do that.
I have tried using sudo usermod -G to add myself back to the groups but to no avail. Any help would be a life saver! Thanks in advance everyone
Niall
p.s. how to you make the terminal entries appear in a little box - cant remember <code> or <quote> or something

---

### Post by skullmunky on 2007-07-09
ah - i think you wanted 

usermod -Ga

for "append", or 

usermod -G --append.   

usermod -G replaces your group membership with only the ones listed right then.  that's why that happened.  don't reinstall yet.

try:

1.  in Gnome: 

System-Administration->Users and Groups
select niall from the list
click "Properties"
go to the "User Privileges" tab
check everything
click "OK"

2. in KDE's System Settings:
click "User Management"
click "Administrator Mode"
select "niall" from the list of users
click "Modify"
next to Secondary groups, click "Select.."
choose the ones you need and click Add to add yourself to them

the gnome way's maybe a little clearer because the group names aren't really that helpful :)

3. use usermod

usermod -Ga adm admin audio cdrom dialout dip fax floppy fuse plugdev scanner tape niall

4. edit /etc/group  

this is the file that has all the group memberships.  add "niall" to the end of all the lines for groups you need to be part of.

---

### Post by mental_drummer on 2007-07-09
Thanks for the help.
1) Users and Groups has dissapeared from my Sytem menue in Gnome

3)niall@sonofyashmak:~$ sudo usermod -Ga adm admin audio cdrom dialout dip fax floppy fuse plugdev scanner tape niall
niall@sonofyashmak:~$ 

i.e. nothing happens

4)i cant sudo gedit the /etc/group file as, again, nothing happens

It seems as if every time I do something with the sudo command there is just no response which makes it very difficult to do anything. Any suggestions?

I think some other people have had this problem so im browsing all the message boards
cheers

---

### Post by bodhi.zazen on 2007-07-09
after changing your group memberships, you need to log out and back into gnome to put them into effect.

---

### Post by mental_drummer on 2007-07-09
Ooh do you think this
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
is useful?
Let you know how i get on

---

### Post by mental_drummer on 2007-07-09
Bingo,:guitar:
the problem was that i was removed from the admin group meaning i couldnt use sudo command (i think) so i rebooted in recovery mode and edited the /etc/groups from there and now everything seems to be peachy. So glad i dint reinstall. thanks for you help
Niall

---

### Post by bodhi.zazen on 2007-07-09
Oh, I missed that, you do not have admin rights ...

OK, either boot the live CD and edit /etc/group from there or boot to the recovery mode (this will give you root access at the command line) and change your groups from there.

Then you can either :

```
init 3
```

Or re-boot

---

### Post by bobmerrick on 2007-07-11
Thanks for this post.
I pulled a similar stunt and the info here saved my bacon.
It's nice to know others are breaking and fixing the same things!
Cheers

---

