---
title: "Ps3 Ubuntu"
date: 2008-04-03
forum: General Help
---

### Post by Hyuukai on 2008-04-03
ok i have already posted this over at psubuntu.com but i need any help i can get really

Ok please be patient with me i am new to Linux and have only really ever been on it a little.

Ok my PS3 boots fine it comes up with kboot so i login ect and i get the default resolution which i try and change and it doesnt work.
So i went through the steps that are on here i press ctrl alt f1 and i go through and find the resolution i want, thats fine i do ps3videomode -v 42 and the text goes alot smaller and shows that it has been able to change the resolution to 1080p which my tv supports. I then do sudo nano /etc/event.d/ps3videomode which brings up the correct thing and i add the lines
start on runlevel 2
exec /usr/bin/ps3videomode -v 42

but when i then try and save this by using ctrl + o it asks me where i am saving it and it comes up with the file im in but when i save it it just says it cant find the file.

I have used this installation of ps3 ubuntu i dunno if that changes anything [https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

I have also tried
install video=ps3fb:mode:42 at the kboot but i get /usr/bin/install : missing destination file operand after 'video=ps3fb:mode:42'

Im probably doing somthing quite stupid but like i said im not very experienced with linux so please help

I have also done what someone asked about on psubuntu which was 

I did ctrl-x then used Y then it came up with the save path and said [Error writing /ect/event.d/ps3videomode: No such file or directory]

---

