---
title: "Trouble with redirection"
date: 2007-07-05
forum: General Help
---

### Post by NuNn DaDdY on 2007-07-05
I recently began shell scripting and I'm writing a small script to give me a rough template for an HTML page but once I type the code for the script and save it in "make_page", I try to redirect this to my file "page.html".  But when I do this I recieve a message stating "command not found".  I'm sure this is more than likely something small and thank you for your help.

---

### Post by pbaumgar on 2007-07-05
> **NuNn DaDdY said:**
> I recently began shell scripting and I'm writing a small script to give me a rough template for an HTML page but once I type the code for the script and save it in "make_page", I try to redirect this to my file "page.html".  But when I do this I recieve a message stating "command not found".  I'm sure this is more than likely something small and thank you for your help.

How are you redirecting make_page to page.html?  Tell us the command you used.

---

### Post by NuNn DaDdY on 2007-07-05
the tutorial says to put :

[me@linuxbox me]$ make_page > page.html

But when I do I get :

corey@NuNn-DaDdY:~$ make_page > page.html
bash: make_page: command not found

---

### Post by pbaumgar on 2007-07-05
> **NuNn DaDdY said:**
> the tutorial says to put :

[me@linuxbox me]$ make_page > page.html

But when I do I get :

corey@NuNn-DaDdY:~$ make_page > page.html
bash: make_page: command not found

So make_page is a shell script?  You'll need to make it executable:

$chmod +x make_page

then run the script and redirect its output to page.html:

$./make_page > page.html

---

### Post by NuNn DaDdY on 2007-07-05
Yep that solved the problem thank you for your help, by the way what effect does the "+x" have on the permissions of the file ?

---

### Post by pbaumgar on 2007-07-05
the +x sets the executable bit on the file for the owner, group and other categories.  

Here's a nice article on linux file permissions:

[http://tldp.org/LDP/intro-linux/html/sect_03_04.html](http://tldp.org/LDP/intro-linux/html/sect_03_04.html)

---

