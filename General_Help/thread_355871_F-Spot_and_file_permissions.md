---
title: "F-Spot and file permissions"
date: 2007-02-07
forum: General Help
---

### Post by chrisccoulson on 2007-02-07
I've recently started using F-spot to organize my photographs, and I'd like to share some photo's between more than one user on my computer. I have set up a shared folder owned by a group called 'shared', and then made all of the photo's readable and writable by all members of 'shared'.

However, when importing the photo's in to F-spot, it appears that only the owner of the photo's can import them. Non-owners (despite being members of 'shared' and having full read-write access to the files) cannot import these photo's at all, as F-spot just refuses to do so.

Does't this behaviour seem a little strange? Has anyone else noticed it? Is there a work around for what I am trying to do?

---

### Post by dudus on 2007-02-21
I just noted this f-spot thing. It seems that the files that were imported using f-spot get 600 permissions. It doesn't make much sense to me. I think that only the files that receive the hidden tag should behave like that. For the other files f-spot should use normal file creation permissions. 

That being said, if you want you can change all the permissions to whatever you like. Because once the files were imported f-spot won't change the permissions again.

---

### Post by jongkind on 2007-02-22
> **chrisccoulson said:**
> 
Does't this behaviour seem a little strange? Has anyone else noticed it? Is there a work around for what I am trying to do?

F-spot works fine for me / my housemembers with photos that are stored in a shared folder (750 access). Importing the photo's is not a problem for the different users. In addition, if they also want to have the same tags that I added to the photo's they can copy the "photos.db" database file to their   ~/.gnome2/fspot directory.

---

