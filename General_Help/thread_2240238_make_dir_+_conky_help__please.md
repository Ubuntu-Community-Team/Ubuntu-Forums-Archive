---
title: "make dir + conky help  please"
date: 2014-08-18
forum: General Help
---

### Post by firas2 on 2014-08-18
Good day

I have been spending to much time to get this conky thing to work , I wish some one can help me out 
 
I  have Ubuntu 14.04     please look at picture   or some one ( if  possible )  Guide me through the steps to get this conky working please 
 
I have been trying and trying and still no luck please look at pic 
[IMG]http://i59.tinypic.com/wwb3pj.jpg[/IMG] 
 
also I am willing to start from the beginning as long as we get it to work 
 
many thanks

---

### Post by nerdtron on 2014-08-18
This is just a directory issue.
Just imagine that your are trying to copy the clock_ring.lua and new-ubuntu-logo.png ~/.conky folder.

Actually, you can do this on the File manager. Just show the hidden files and you will the .conky folder on you home folder.
Now where did you extracted the ubuntu-lua.tar.gz? Go inside that folder and you will the files clock ring and ubuntu logo.
Select them and COPY. Now go to your home folder (show hidden files) and you'll see .conky folder.Go inside it and PASTE.

Next step, on your home directory, edit the .conkyrc file. (Last line on your screenshot)

---

### Post by firas2 on 2014-08-18
Thanks for the fast reply   as far as the conky folder i had to creat it , but it looks to me there is more then 1 home directory ( forgive me im new )   Question   is home directory  where home/     or is it home/user ???

i will do ur tips and see what goes on

---

### Post by nerdtron on 2014-08-18
Your home directory should be /home/username. Just click the Home folder and you should be there.

You have to create the conky folder? It already says in your screenshot that .conky folder already exists. Remember to show hidden files as the folder starts with a . (dot). This means it is hidden.

---

### Post by firas2 on 2014-08-18
Does this look right ??  if yes  it is still not working same error  in terminal

[IMG]http://i61.tinypic.com/2uemnpc.jpg[/IMG]

---

### Post by firas2 on 2014-08-18
[IMG]http://i60.tinypic.com/33xk4cw.jpg[/IMG]

this is how it looks like  not sure if this is correct or not

---

### Post by nerdtron on 2014-08-18
conky rings and ubuntu logo is correct. The file .conkyrc should be in /home/whome

Can you give the link on the tutorial you followed?

---

### Post by firas2 on 2014-08-19
> **nerdtron said:**
> conky rings and ubuntu logo is correct. The file .conkyrc should be in /home/whome

Can you give the link on the tutorial you followed?

Yes sure   

[http://xmodulo.com/2013/12/install-configure-conky-linux.html](http://xmodulo.com/2013/12/install-configure-conky-linux.html)

Im just starting to think   That Maybe It will take me for ever to figure this thing out 

one other thing please    In terminal every time i try to install something or do an upgrade    

it says   maybe u should use the -f command   but i dont know where to use the  -f after before  or where :mad:

---

### Post by firas2 on 2014-08-19
Ok  I really really  want to find out  is it me or the Distro  

So if ur willing to stick with me and help me out all the way  ,, I am willing to start all over 

So here is a Different version of Ubuntu  as u see in the pic   and when I type conky  I get this little black screen ,  Does this mean conky is installed ???  If so  then why cant I find  .conky in my home folder ??
as u see in my second Picture   this is what is driving me crazy   ,, and when I make a >conky folder in my home folder   I get Folder already exists

 [IMG]http://i60.tinypic.com/3176w48.jpg[/IMG]

[IMG]http://i61.tinypic.com/prd6t.jpg[/IMG]

---

### Post by nerdtron on 2014-08-19
Conky is already installed.

Now let's see if what conky files and folders are already in your home folder. Post the output of the following.
```
cd
pwd
ls -lah | grep conky
```

If I remember correctly, the .conkyrc file is the default conky configuration file while the .conky folder is not created by default since there is no use for it.

---

