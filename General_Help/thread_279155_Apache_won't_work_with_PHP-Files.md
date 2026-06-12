---
title: "Apache won't work with PHP-Files"
date: 2006-10-17
forum: General Help
---

### Post by chaosgeisterchen on 2006-10-17
Hi there,

I long for continuing working with my *.php-files on my kubuntu machine. I have installed and started the newest version of apache properly. I created a folder named **public_html** in my $home and I can access it without any problem at the adress **localhost/~chaosgeisterchen** - but when I select any of those PHP-pages to be opened, some Qt-dialog-window pops up, it's reading:

[b]Open $file?
Type: application/x-httpd-php[/b]

Could be some bad translation as my kubuntu machine's locale is de_AT. But I did not find out how to work it out.. I already tested to chmod 777 both files and directory, does not help, restarted apache several times, but apache itself should be running flawless I assume. I deleted overhead-*.desktop-files in my ~/.kde - directory as that cleared up some mess I had earlier with corrupted MIME-base.

Whatelse can I to in order to solve this annoying problem?

I would be very thankful if any of you could help me.

Thanks in advance,

chaosgeisterchen

---

### Post by az on 2006-10-17
> **chaosgeisterchen said:**
> Hi there,

I long for continuing working with my *.php-files on my kubuntu machine. I have installed and started the newest version of apache properly. I created a folder named **public_html** in my $home and I can access it without any problem at the adress **localhost/~chaosgeisterchen** - but when I select any of those PHP-pages to be opened, some Qt-dialog-window pops up, it's reading:

[b]Open $file?
Type: application/x-httpd-php[/b]

Could be some bad translation as my kubuntu machine's locale is de_AT. But I did not find out how to work it out.. I already tested to chmod 777 both files and directory, does not help, restarted apache several times, but apache itself should be running flawless I assume. I deleted overhead-*.desktop-files in my ~/.kde - directory as that cleared up some mess I had earlier with corrupted MIME-base.

Whatelse can I to in order to solve this annoying problem?

I would be very thankful if any of you could help me.

Thanks in advance,

chaosgeisterchen


Do you have libapache2-mod-php5 installed?

---

### Post by mjziegle on 2006-10-17
Follow the LAMP setup instructions in wiki.  Also check your user permissions and default directories in /etc/apache2/apache2.conf

---

### Post by chaosgeisterchen on 2006-10-17
> **azz said:**
> Do you have libapache2-mod-php5 installed?

Hmh, I have to learn several things before I start developing under Linux. First that Apache is not like XAMPP where everything is already included.

I installed the mod-php5 and everything's fine. I will remember.

Thanks a lot.

@mjziegle:

It's all correct.

---

