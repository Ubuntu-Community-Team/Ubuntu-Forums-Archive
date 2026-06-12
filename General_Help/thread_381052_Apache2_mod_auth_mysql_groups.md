---
title: "Apache2 mod_auth_mysql groups"
date: 2007-03-10
forum: General Help
---

### Post by GeraldR63 on 2007-03-10
Hello,

I've installed Apache 2.0 and mod_auth_mysql. I'm able to use it for user authentification but not for group authentification.

I'm testing authentification via a MySQL database schema I already use for e-mail users using the schema tables installed by postfix admin. 

I've added one column "group" to the "mailbox" table of the postfix database to allow authentification via groups.

I've used the column types  as described at [http://www.howtoforge.com/mod_auth_mysql_apache2_debian]("http://www.howtoforge.com/mod_auth_mysql_apache2_debian").

For first tests I used a .htaccess file. This looks like

=========.htaccess begin
AuthMYSQL on
AuthMySQL_Authoritative on
AuthMySQL_Host localhost
AuthMySQL_User <USER>
AuthMySQL_Password  <PASSWORD>
AuthMySQL_DB postfix
AuthMySQL_Password_Table mailbox
AuthMySQL_Group_Table mailbox
AuthMySQL_Empty_Passwords off
AuthMySQL_Encrypted_Passwords On
AuthMySQL_Encryption_Types Crypt_MD5 Plaintext Crypt_DES  PHP_MD5
AuthMySQL_Username_Field name
AuthMySQL_Password_Field password
AuthMySQL_Group_Field group

AuthName "myName"
AuthType Basic
#require valid-user  uncomment this work!
# require group 2 uncommenting this does not work
=========.htaccess end

I can use the "required valid-user" tag for authentification. This works fine. If I uncomment "require group" than I got failures:

/var/log/apache2/error.log:
[Sat Mar 10 17:56:00 2007] [crit] Group query failed!

/var/log/mysql/mysql.log:

070310 17:56:00   25447 Connect     root@localhost on postfix
                  25447 Query       SELECT password FROM mailbox WHERE name='sysop'
                  25447 Query       SELECT count(*) FROM mailbox WHERE name='sysop' and FIND_IN_SET('2',group)


Trying to use the second SQL in MySQL results in a syntax error. For example:


SELECT count( * )
FROM mailbox
WHERE name = 'sysop'
AND FIND_IN_SET( '2',
GROUP )

MySQL message: Documentation
#1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'group)' at line 1 

This seems to be really false. It seems that column group have to be of type 'set' but I do not know how to create this type of column. I've searched the documentation but found nothing and in my opinion I should follow the official documentation.

What to do?
Another question:
Which Version is the current mod_auth_sql I got using apt-get for Edgy Eft?


I've found a lot of very interesting configuration options for mod_auth_mysql (related to the groups configuration) which seem not to work with the actual release. So I tried to download release 3.0 of mod_auth_mysql and to build the shared library but I was not able to compile a new one from source because there is no command line utility called "APXS" as described in the documentation of  mod_auth_mysql-3.0.0.tar.gz and I found no way to install it via "apt-get".

Now I do not have any idea how to solve this problem by myself. In my opinion I've done all I could. Would be very nice to get some help with this.



kind regards
Gerald

---

### Post by GeraldR63 on 2007-03-10
I've found the solution for this issue by myself.

The column group should be renamed to groups to keep it as simple as possible.
Than I changed the type of the column to set.

ALTER TABLE mailbox CHANGE `groups`
`groups` SET('0','1','2','3') NOT
NULL;

and voila it works. The documentation at [http://www.howtoforge.com/mod_auth_mysql_apache2_debian]("http://www.howtoforge.com/mod_auth_mysql_apache2_debian") seems to be false or for a different release.


I've tested this using Ubuntu Edgy Eft, Apache 2.0, MySQL 5.x, PostFixadmin  as offered by Ubuntu via apt-get.

---

