---
title: "I need PHP 4 and MySQL 4 in Feisty"
date: 2007-05-06
forum: General Help
---

### Post by Peter Mount on 2007-05-06
Hi

In Dapper and Edgy I was able to get PHP4 and MySQL 4 with the aid of this page:

[https://help.ubuntu.com/community/ApacheMySQLPHP/](https://help.ubuntu.com/community/ApacheMySQLPHP/)

I installed Feisty and now of course I found that PHP4 and MySQL 4 aren't available for Feisty.

 My web host uses PHP4 and MySQL 4. I sent them an email today asking when they'll upgrade to PHP5 and MySQL5. I expect a reply in the next working day. I prefer not to have to change web hosts. They have cheap Linux plans that I can afford plus I've got client's web sites hosted with them as well and I don't want to disrupt them if I can help it.

I've looked at this page:

[http://jdv.hopto.org/index.php?/archives/84-Ubuntu-Feisty-with-Apache-2.2,-PHP4-with-FastCGI-and-MySQL-support.html](http://jdv.hopto.org/index.php?/archives/84-Ubuntu-Feisty-with-Apache-2.2,-PHP4-with-FastCGI-and-MySQL-support.html)

It shows how to install PHP4 but not MySQL4.

In the mean time I can install Edgy on another hard drive.  Depending on what my web host says about when they upgrade PHP and MySQL I might have to seriously start looking at other distros like Fedora. I found a web page that has instructions on installing PHP4 and MySQL 4 at:

[http://www.transcendingthought.com/content/view/31/42/](http://www.transcendingthought.com/content/view/31/42/)

However my past experiences with Fedora have me worried about it's stability even in the latest version. I'd much rather keep using Kubuntu if I can.

Thanks

---

### Post by Phlosten on 2007-05-06
Can you install a Dapper development environment in VMWare or VirtualBox to solve the issue?

Seems odd to me that they have not upgraded to at least MySQL 5.

---

### Post by Peter Mount on 2007-05-06
> **Phlosten said:**
> Can you install a Dapper development environment in VMWare or VirtualBox to solve the issue?

Seems odd to me that they have not upgraded to at least MySQL 5.

I can put Edgy on a seperate hard drive. I have to look into VMWare and VirtualBox.

I got an email back saying my web host might take up to a year to upgrade to PHP5 and MySQL 5. As long as I can replicate the hosting environment on my computer I'll be happy.

Have fun

---

### Post by acascante on 2007-07-26
What I did was to download mysql4.1 ubuntu packages from here:

[http://security.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-4.1/](http://security.ubuntu.com/ubuntu/pool/universe/m/mysql-dfsg-4.1/)

all three packages, client, client-lib and server and installed starting with client-lib there could be some unresolved dependencies I resolved those with apt-get install using the same name reported by dpkg --install.

Now I have mysql 4.1 in feisty, I heard they don't include 4.1 because Mysql guys stop support on that version; however, for some applications 5.0 is not an option due incompatibilities in the SQL language implementation.


This is the command I used to resolve the dependencies:

$ sudo apt-get install  libnet-daemon-perl libplrpc-perl libdbi-perl libdbd-mysql-perl

then I installed client lib deb downloaded from the site above:

   sudo dpkg --install libmysqlclient14_4.1.15-1ubuntu5_i386.deb

then the client itself:
 
   sudo dpkg --install mysql-client-4.1_4.1.15-1ubuntu5_i386.deb

finally the server:

   sudo dpkg --install mysql-server-4.1_4.1.15-1ubuntu5_i386.deb 

you can use this parameter  -s in any of the above commands to try the command like a dry test, it won't do it really just will try it out.

The order don't matter much as long you resolve all dependencies...

---

