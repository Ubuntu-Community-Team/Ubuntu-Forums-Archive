---
title: "How can I set up an enviroment to work with PHP etc."
date: 2006-11-01
forum: General Help
---

### Post by thenetduck on 2006-11-01
Hi, 
  I program in C/C++ and Java and want to explore the "web" side of things. I need to make myself a sandbox so to speak to work in on my machine, but don't know the best way to go about it. I want to basically be able to make a web page that can read Javascript, PHP and MySQL. Right now im running Ubuntu Edgy. 
   Would anyone be able to help me out in getting this set up? Or at least point me in the right direction. Most of the things I have found are related to Dapper.....

 Thanks, 
 
 The Net Duck

---

### Post by ciscosurfer on 2006-11-01
You can set up an [xampp environment]("http://ubuntuforums.org/showthread.php?t=223410&highlight=xampp") (not suitable for production...don't use it to serve out content over the web) or you can set up a fully-fledged [LAMP environment]("https://help.ubuntu.com/community/ApacheMySQLPHP").  Have a good time!

---

### Post by ciscosurfer on 2006-11-01
As far as things that are related Dapper, most often you can also adapt the instructions (if not simply use them verbatim) on Edgy.  Enjoy!

---

### Post by Zeroangel on 2006-11-01
A LAMP environment is perfect for working on web applications. What I did was install the LAMP stack (Apache, MySQL, PHP, phpMyAdmin). With that done, you will have the ability to develop PHP apps and websites. To make it easier however, you will probably want to make your projects folder a little more accessable.

To do so rename the /var/www/ folder to something else, and create a /var/www/ symlink to my /home/$USER/Projects folder You can that by running these commands:
```
mkdir /home/$USER/Webdev
mkdir /home/$USER/Webdev/Projects
sudo mv /var/www /var/www-bak
sudo ln -s /home/$USER/Webdev/Projects /var/www
sudo chown $USER /var/www
```With that done, you should have easier access to your web projects. However, you will now need to edit them. If you're using Kubuntu, you can use Kedit or Kwrite, both of these are fast (like 'notepad' but for linux) though you can use kate (slower, but heavier on features). In Ubuntu/GNOME you will want to use gedit. If you really want to get serious (ie: if you are developing a full website with PHP) then you will be better off using a full scale IDE like Bluefish or Quanta.

For that, I highly recommend Quanta. Bluefish comes by default on Ubuntu but Quanta is far more professional. Quanta, for example has very powerful project management features (ie: two click uploading), syntax highlighting, autocomplete, validation, debugging, and plenty of other features needed out of a full-scale IDE. However, it is designed for KDE, so that might be a factor if you're using Ubuntu.

---

### Post by intrepid_geek on 2007-05-31
Is the above mentioned Secure??

---

