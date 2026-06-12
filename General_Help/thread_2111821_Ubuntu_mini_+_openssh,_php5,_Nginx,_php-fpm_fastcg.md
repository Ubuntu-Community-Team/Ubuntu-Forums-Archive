---
title: "Ubuntu mini + openssh, php5, Nginx, php-fpm fastcgi, Trying to install phppgadmin"
date: 2013-02-03
forum: General Help
---

### Post by xekon on 2013-02-03
I installed the Ubuntu 12.10 minimalist iso from usb flash
help.ubuntu.com/community/Installation/MinimalCD

then I installed some other things I need:
sudo apt-get install openssh-server
sudo apt-get install python-software-properties
sudo apt-get install software-properties-common
sudo apt-get install nginx php5 php5-fpm php-pear postgresql phppgadmin
sudo apt-get update
sudo reboot

I then followed this guide:
[http://www.networkinghowtos.com/howto/installing-nginx-php-and-mysql-on-ubuntu-12-04-lts/](http://www.networkinghowtos.com/howto/installing-nginx-php-and-mysql-on-ubuntu-12-04-lts/)

and I have nginx installed and working, the only thing I did in addition to that guide, was I modified the root line, so I could have my web files in my user folder, that way I wouldn't have to worry about setting permissions

mkdir -p /home/webs/public_html/jitest.com/{public,private,log,backup}

root /home/webs/public_html/jitest.com/public;

after a restart:
sudo /etc/init.d/php5-fpm restart
sudo service nginx restart

NGINX is working, and phpinfo() works :)

**Now my next hurdle is getting postgresql configured**, I took a look at this guide: [https://wiki.archlinux.org/index.php/Phppgadmin#NGINX_Configuration](https://wiki.archlinux.org/index.php/Phppgadmin#NGINX_Configuration)

only problem is it shows **phppgadmin** as being installed to **'/usr/share/webapps/phppgadmin'** **but I'm not seeing it there** after installing the phppgadmin package.

**EDIT:**
 found this command:
   **dpkg -L phppgadmin**

and after running it shows that it IS installed in /usr/share/ the issue was WinSCP did not refresh the directory contents, right click and refresh and now I can see it.

---

