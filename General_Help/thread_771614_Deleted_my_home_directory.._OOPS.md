---
title: "Deleted my home directory.. OOPS"
date: 2008-04-27
forum: General Help
---

### Post by ghost_ryder35 on 2008-04-27
Ok so as the story goes I deleted my home directory... Kind of.  I have attached a screen shot for your review.  I have tried to delete it from the recycling bin and what not with no success (computer runs perfectly fine otherwise).  I have also tried it via the command line as shown below.  I can add things to the /.trash and delete them but the directory will not go away.  I have also tried logging in on run level 3 and logging in as root (I have set the root password) and deleting the /.trash with no success.  Weird thing is I can click on my username and Desktop an infinite amount of times (please refer to screen shot at location bar)

```

sudo rm -rf ~/.Trash/* 
sudo rm -rf ~/.trash/*

```no success.  So i went looking in my home directory and i DO NOT HAVE A TRASH FOLDER!!!!  Also posted a screen of that.


/home In Trash:
 [[IMG]http://img209.imagevenue.com/loc254/th_44014_test_122_254lo.jpg[/IMG]]("http://img209.imagevenue.com/img.php?image=44014_test_122_254lo.jpg")

No /.Trash:
 [[IMG]http://img216.imagevenue.com/loc1/th_44451_test1_122_1lo.jpg[/IMG]]("http://img216.imagevenue.com/img.php?image=44451_test1_122_1lo.jpg")

This is kind of funny but I dont like seeing paper in my ./trash (can) HELP!

---

### Post by ghost_ryder35 on 2008-04-27
bumpidy bump :guitar:

---

### Post by Ralphie on 2008-04-28
are you able to just replace it? like drag it outta there and back into where the home directory should be?

Maybe there is some sort of block from deleting your whole home directory. you should just put it back where it goes... if possible. Otherwise it sounds like a bug or something

---

### Post by ghost_ryder35 on 2008-04-28
> **Ralphie said:**
> are you able to just replace it? like drag it outta there and back into where the home directory should be?

Maybe there is some sort of block from deleting your whole home directory. you should just put it back where it goes... if possible. Otherwise it sounds like a bug or something
No.  I cant drag it out.... But my /home/sopnpo is still were it should be.  I just have an extra copy in the ./trash.  No good.  Any more tips?

---

### Post by Islington on 2008-04-28
er ```
sudo nautilus
``` now can you drag it back?

---

### Post by ghost_ryder35 on 2008-04-28
nope. But I figured out how to fix it :)  Clean install babies :)  Have been wanting to do it for a while now.  This thing has been updated from Feisty, to Gutsy, to Hardy beta, and now the Final Hardy.  Might as well download the RTM cd and clean install.  I already backed up my home directory anyways.  Whatever :)

Screen shot for ya
 [[IMG]http://img214.imagevenue.com/loc444/th_93916_sdf_122_444lo.jpeg[/IMG]](http://img214.imagevenue.com/img.php?image=93916_sdf_122_444lo.jpeg)

---

