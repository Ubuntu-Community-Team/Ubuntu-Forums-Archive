---
title: "unixODBC settings for Oracle"
date: 2014-11-08
forum: General Help
---

### Post by abhiquiet on 2014-11-08
Hi everyone. 

I am currently using Ubuntu 14.04.1 LTS version and have deployed oracle v 11.2 instant client successfully. 

I have also install unixODBC and successfully configured to access the databases from my machine. 

I am getting no error while connecting oracle data base using the isql in my user area. 

But I am not able to access the oracle database using my web application running under www-data group and i am getting the error stating 
"ERROR [01000] [unixODBC][Driver Manager]Can't open lib '/usr/lib/oracle/11.2/client64/lib/libsqora.so.11.1' : file not found"

I have checked the file pointed out in the error is existing in the machine. 

I feel there is some issue with regard to access of the file to the usergroup www-data trying to connect to the database using the web application. 

i have also tried giving full access rights through chmod 777 /usr/lib/oracle/11.2/client64/lib/libsqora.so.11.1

but same has not given me any success. 

Can any body help me setting up unixodbc to connect oracle database using my web application. 

Regards. 

Abhinav

---

### Post by test051102 on 2015-02-04
Just read "Integrate Oracle Libraries" at [https://help.ubuntu.com/community/Oracle%20Instant%20Client](https://help.ubuntu.com/community/Oracle%20Instant%20Client). You need to add some required environment variables. These environment variables need to be declared "system wide".

It's a shame for Oracle that there are still no Debian packages available these days. It's strange that there are so many hacks to get such a simple thing running.

---

### Post by Jean_Robertson on 2015-09-11
Hello,
The error message is deceptive.
Once the oracle instant  client odbc package installed -- which provides  /usr/lib/oracle/11.2/client64/lib/libsqora.so.11.1 -- that library has  its own library dependencies.
So if you do:
ldd /usr/lib/oracle/11.2/client64/lib/libsqora.so.11.1
you will get an error message:
libodbcinst.so.1 => not found
Here, the oracle library is looking for a unixODBC library.
Once the libodbc1 package is installed, the oracle library finds its dependencies.

There  is no use changing permissions on  /usr/lib/oracle/11.2/client64/lib/libsqora.so.11.1. It will not improve  anything and it is a security hole.

---

