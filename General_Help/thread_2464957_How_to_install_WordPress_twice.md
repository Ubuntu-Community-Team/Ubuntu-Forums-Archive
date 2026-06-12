---
title: "How to install WordPress twice?"
date: 2021-07-17
forum: General Help
---

### Post by jcdenton1995 on 2021-07-17
Hello all,

I want to install a second WordPress instance to allow me to host multiple sites; I already installed WordPress once via apt-get, and I can't imagine there is a way in which I can install it again via the package manager. Is the best course of action to download the .tar.gz archive from the wordpress website and just install it directly? That seems kind of messy and I'd prefer it if there was a more sophisticated method of managing the two instances.

Any ideas?

---

### Post by Holger_Gehrke on 2021-07-17
The version of WordPress in the repositories can be severely behind the times depending on the version of Ubuntu you're running. For example on Focal you get 5.3.2 from the repositories while you'll get 5.7.2 from wordpress.org. With WP being such a favourite target of hackers, I wouldn't want to use anything less than the very latest.

I don't have much experience with WordPress, but back when I ran a site using Typo3 best practice was to have the code in a directory outside of DocumentRoot once and have symlinks to specific directories in the code directory in the websites' directories. This gives you the option of updating the code by installing the new version into a new directory and just changing the symlinks.

Holger

---

### Post by jcdenton1995 on 2021-07-17
> **Holger_Gehrke said:**
> 
I don't have much experience with WordPress, but back when I ran a site using Typo3 best practice was to have the code in a directory outside of DocumentRoot once and have symlinks to specific directories in the code directory in the websites' directories. This gives you the option of updating the code by installing the new version into a new directory and just changing the symlinks.


That's interesting, thanks. I'm not actually exposing the site to the wider internet, I just have WordPress installed locally, along with the requisite stack, so that I can actually build the site on my own computer without paying for hosting, and then the plan is to migrate it to a hosting providers server when it is done (that's the theory anyway). My Apache server is configured to only accept requests from my local machine.

Also, very interesting what you say about the version difference between the repository and the latest actual release, and I'll bear that in mind for the future in case I decide to host anything myself...

---

### Post by mIk3_08 on 2021-07-17
You can install other WordPress on your WordPress website by 
example: yoursite.com/newWordPress or 
newWordPress.yoursite.com 
depending what you want. 
But you must have to consider creating a separate/new sql database when doing it for safety purposes of your databases. 
This is a little bit tricky but fun. 
Enjoy, Good Luck!

---

### Post by dragonfly41 on 2021-07-17
I installed XAMPP separately from usual Apache2 server, in /opt/lampp then separately installed WordPress into /htdocs.
Just bear in mind that the XAMPP processes will conflict with any running instances e.g. Apache2 and MySQL
so in starting XAMPP (LAMPP) I run these commands first:

[FONT=monospace][COLOR=#000000]sudo /etc/init.d/apache2 stop[/COLOR]
sudo /etc/init.d/mysql stop
sudo /opt/lampp/manager-linux-x64.run

then in the LAMPP GUI, start all servers (Apache abd MySQL). 
LAMPP (and WordPress) then runs on defined port such as 8000.

[/FONT]

---

### Post by mIk3_08 on 2021-07-19
For my Ubuntu Server I used NGINX.
to enable it I command nginx by using command code to enable it 
```
sudo systemctl enable nginx.service
```
Then After I enable it I start the service by using this command below;
```
sudo systemctl start nginx.service
```
in my /usr/share/nginx/html
here I put my web data to run my website
But I reconfigure the root location of my site to where it point to the location of my web data.
/usr/share/nginx/html
```
 root  /usr/share/nginx/html;
```
where the nginx is point my web location data.

---

