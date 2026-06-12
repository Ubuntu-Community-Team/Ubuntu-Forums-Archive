---
title: "Access to administrator rights is denied."
date: 2007-02-01
forum: General Help
---

### Post by shriniketsarkar on 2007-02-01
Hi ,
     i am facing a problem in accessing the services and the networking options in ubuntu.When ever i type sudo admin-services it does not open any thing and also it flashes a message saying "Could Not Open ......""U may not have the administrator rights for it"  i am not remembering the exact msg displayed but it said that i didnt have the adminstrative rights.
    Later logged in with root as the user ...but still it gives the same msg.
       I am not getting what to do ?Is there any other super user than the root who can change or at least reset all the settings...and previledges....for ubuntu?
        I even tried by creating a new user under the group root and making him the administrator but for that user too it gives the same error msg.
 

         Please let me know if this has any solution or i need to format and reinstall again ....?

---

### Post by frafu on 2007-02-01
Hello, 

The Accessibility Forum being related to Assistive Technology, I have moved this thread to the General Help Forum where it is more appropriate and where it has a greater probability to receive answers. 

Have a nice day. 

Francesco

---

### Post by bodhi.zazen on 2007-02-01
> **shriniketsarkar said:**
> Hi ,
     i am facing a problem in accessing the services and the networking options in ubuntu.When ever i type sudo admin-services it does not open any thing and also it flashes a message saying "Could Not Open ......""U may not have the administrator rights for it"  i am not remembering the exact msg displayed but it said that i didnt have the adminstrative rights.
    Later logged in with root as the user ...but still it gives the same msg.
       I am not getting what to do ?Is there any other super user than the root who can change or at least reset all the settings...and previledges....for ubuntu?
        I even tried by creating a new user under the group root and making him the administrator but for that user too it gives the same error msg.
 

         Please let me know if this has any solution or i need to format and reinstall again ....?

Hard to know.

Could you open a terminal and type in:

```
sudo -i
```

You should be given access to root (after entering your PW).

copy and paste any error message ...

---

### Post by mhwelsh on 2007-02-02
Yes but even with monitor showing "root@computername" I still get a notice saying that I am not allowed to reconfigure eth0 in Network Tools.

martin welsh

---

### Post by bodhi.zazen on 2007-02-02
I am afraid you will need to give more details on what you are doing.

If you are root ( "root@computername" ) you have admin access.

So the problem is not "Access to administrator rights is denied" but rather seemingly a problem configuring you network ?

I would help if you could describe what you are trying to do exactly, hardware involved, and 
command and terminal output, copy and paste if you could, change you computer info if yo like.

You may also want to start a new thread with a more appropriate (descriptive) title.

HTH

---

### Post by shriniketsarkar on 2007-02-02
Hi ,
     I tried what u said ..it even gives me the root login...but still the same msg ....I am sending u the error image that i get..please have a look...
      Let me know if anything else can be done.....

---

### Post by shriniketsarkar on 2007-02-02
Hi 
    Actually the problem is a bit diff .....Even when i log in with root as the user ....it logs me in successfully but when i open any service or say when i fire a command in the terminal like services-admin then it gives me some error......
   I am sending u the error image that i get..please have a look...
Let me know if anything else can be done.....
       Also this same happenes when i try to open the networking console from menu....

---

