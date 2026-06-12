---
title: "File Permissions issue??"
date: 2007-01-25
forum: General Help
---

### Post by tiger.woods on 2007-01-25
I wanted to ask a question or 2 with regard to permissions in ubuntu or in Linux for that matter.

1) When installing Ubuntu I was asked to create a user (Jim) and password. I assumed this was not a root user is that a correct assumption?

2) Assuming the user I created was not a root user then the 'Home' folder associated with that user "Jim" should belong to that user "Jim", correct?

3) After creating a subfolder (/NewFolder) in the users '/Home' folder. When saving files to "/NewFolder" shouldn't "Jim" have the permissions to change any or all of the files in that folder or even the permissions of the folder "/NewFolder"?

Now my problem, I downloaded Mythtv into /Home/NewFolder/Myth while logged in as "Jim" and the files that were downloaded have "root" permissions on them? I don't understand how that happend???

 How can I change this so that "Jim" always has permission in his /Home folder?

Thanks,

---

### Post by Goober on 2007-01-25
Hello, 

I know bits and pieces to be able to help you ... 

1 - No, this is not the root user, that is what I call the "regular" user.  The difference is that the root user can do more stuff, change administrative settings and such, entering the password you created when required.  In a Terminal, type "sudo" before whatever else you type if you need to be the root user.  You can use the Nautilus File Browser as root to browse your files as the root user.  Type the following into a Terminal to start Nautilus in root mode:

```

gksudo nautilus
```

2 - Yes. 

3 - Yes, as long as they are not available only to the root.  

I learned a tip, if you have a file (Say a .doc) that you want to allow Jim to use, and it was created in root mode, go into Nautilus in root mode, right-click on the file, and select "Properties" at the bottom.  The click on the Permissions tab.  Change the "Owner" and "Group" to Jim, and the tabs underneath to Read and Write.  That will allow Jim to alter and change that file, and access it, as required.

I hope that helps.

---

### Post by aysiu on 2007-01-25
That should read *gksudo nautilus*, not *gksodu nautilus*.

---

### Post by Goober on 2007-01-25
Right.  Thank you aysiu.  That explains why it didn't work for me that last time ...

---

### Post by Ptero-4 on 2007-01-25
Also some apps that you download from the web (like MythTV) will come with the permissions set to root, that's because the root account is the only account that comes standard in all linux distros, but this doesn't affect the permissions on files you create yourself.

---

### Post by poohbear1616 on 2007-01-25
Placing anything directly into /home would be given root ownership. which would require being root everytime you wanted to access that item,and I don't think changing owner on /home will work very well. When you used Jim as sign in name a directory of /home/jim should have been created, Put goodies their for jim to be owner.

---

