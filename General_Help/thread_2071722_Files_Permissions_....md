---
title: "Files Permissions ..."
date: 2012-10-16
forum: General Help
---

### Post by CCgirl6690 on 2012-10-16
Hello i have ubuntu 12 and backtrack 5 dual boot on my lappy . i coppied some files and folders to my ubuntu home folder on backtrack ,  but when on ubuntu i tried to reach em  it said i dont have root permission to reach em and there's a lock icon on the folders , i can use em on backtrack thou  so my question is ... how can i access those files on ubuntu  or set the permissions in a safe way  thank you .....................

---

### Post by jerrrys on 2012-10-16
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

gksudo nautilus

Then change file permissions with right click and properties.

More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+file+permissions&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+file+permissions&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by CCgirl6690 on 2012-10-16
but my files have lots of folders and sub folders , i cant go to each one of them one by one and give the postgres premission ... are there any way to do this all in one operation?    thankz?

---

### Post by magnusk on 2012-10-16
In top folder:
sudo chown myusername:mygroupname * -R
This will change ownership recursivly for all subfolders/files.

---

### Post by CCgirl6690 on 2012-10-16
Thank you , but do i have to do that on backtrack where i have access to those files or on ubuntu 12?  and what is groupe name  i made a mistake and in backtrack type chmod -R 660 my whole ubunu home folder" then when i tried to get back on ubuntu it gave me "could not write bytes :broken pipe" error and i fixed it with pcman file manager ,  pcman file manager dont apply all the setting to all the subfolders and files thou. but atleast it fixed my ubuntu 12 and now im back on it.... so would you please give me more detailed command lines,noob friendly , cuz i barely work with commands,,,, thank you

---

### Post by jerrrys on 2012-10-16
First link  

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=what+is+my+user+group+name&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=what+is+my+user+group+name&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by CCgirl6690 on 2012-10-16
looks like you're into googlubuntu alil to much . my case is different but thanks for atleast letting mw know what googlubuntu is lol

---

### Post by jerrrys on 2012-10-16
> **CCgirl6690 said:**
>  and what is groupe name

Sorry, it looked like the right answer.  Good luck

---

