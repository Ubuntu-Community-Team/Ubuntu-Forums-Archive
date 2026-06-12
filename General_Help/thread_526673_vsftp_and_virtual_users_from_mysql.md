---
title: "vsftp and virtual users from mysql"
date: 2007-08-15
forum: General Help
---

### Post by lwranger3 on 2007-08-15
I have been attempting to set up vsftp on a Ubuntu system using virtual users authenticated against a mysql database. 

I have been using the following guide:

[http://www.howtoforge.com/vsftpd_mysql_debian_etch]("http://www.howtoforge.com/vsftpd_mysql_debian_etch")

Although I have followed the instructions to the letter, every time I try to establish a connection I get '530 Login incorrect'. Any clues? Are there changes I should be making that are specific to Ubuntu? 

Thank you in advance,

lwranger3

---

### Post by PaulFr on 2007-08-16
I used the Falko guide on howtoforge (**[http://www.howtoforge.com/virtual_users_and_domains_with_postfix_debian_etch_p3](http://www.howtoforge.com/virtual_users_and_domains_with_postfix_debian_etch_p3)**) to install Postfix, and one thing which was very useful to me was to first set **crypt=0** in the /etc/pam.d/<file> and enter a plain text password in the MySQL table. So I could be sure that there was no encryption algorithm mismatch issue.

From the documentation at the pam_mysql site(**[http://pam-mysql.sourceforge.net/Documentation/package-readme.php?seemore=y](http://pam-mysql.sourceforge.net/Documentation/package-readme.php?seemore=y)**)> crypt (0)

    Specifies the method to encrypt the user's password:

        * 0 (or "plain") = No encryption. Passwords stored in plaintext. HIGHLY DISCOURAGED.
        * 1 (or "Y") = Use crypt(3) function
        * 2 (or "mysql") = Use MySQL PASSWORD() function. It is possible that the encryption function used by pam-mysql is different from that of the MySQL server, as pam-mysql uses the function defined in MySQL's C-client API instead of using PASSWORD() SQL function in the query.
        * 3 (or "md5") = Use MySQL MD5() function

md5 (false)

    If set to "true", use MD5 by default for crypt(3) hash. Only meaningful when crypt is set to "Y".
So I would suggest you first try with crypt=0 and then once that works, then add the appropriate value for crypt. Hope this helps.

P.S. Also, please test from the same machine first before verifying from outside your LAN.

P.P.S. The Falko guide on Postfix with virtual users uses **crypt=1** and the comment on **crypt=2** in the above quote seems to suggest possible incompatibility.

---

### Post by lwranger3 on 2007-08-16
I made the changes, removing the PASSWORD function on the password field in the MySQL database so that passwords are stored in plain text, and I changed the value of CRYPT in the PAM file to '0'. A connection was successfully established! Next step is to perform further testing of CRYPT...

Thank you for the advice - much appreciated.

---

### Post by OffAxis on 2007-09-13
Thanks for the **crypt** suggestion from over here, too; it helped me figure out that it wasn't the password function or encryption that was blown in my install, it was the fact that i didn't have the libpam-mysql package installed. whoops.

For anyone who needs it:

```
sudo aptitude search libpam-mysql
```
(an **i** means that it's installed) 

If it's not installed
```
sudo apt-get install libpam-mysql
```

also, vsftpd seemed to do a funny thing when I tried to restart it with 
```
sudo /etc/init.d/vsftpd restart
```
in that it wouldn't actually restart the first time I ran it (not in the running processes and all ftp connection attempts would be refused) but it would restart and function normally after restarting vsftpd a second time.
I don't know why, but I'm going with it.

I used the [howtoforge ]("http://www.howtoforge.com/vsftpd_mysql_debian_etch")tutorial by falko as well.

---

