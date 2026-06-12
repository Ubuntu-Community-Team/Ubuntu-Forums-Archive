---
title: "Difficult samba problems :("
date: 2007-07-18
forum: General Help
---

### Post by Darth_tater on 2007-07-18
I have decided to re do my home file server and now I need some help with samba.  I have many issues, but I think I will be able to get all but these two.

1)	How can I make certain folders un available to certain users.  EG: inside a public directory (for this example let’s call it A)  there are two folders (B and C)  I want B to be available for everybody but I only want certain users to be able to access directory C.  there has to be way to do this… but I don’t know how.
2)	Also, what create mask do I need so that each folder/file  any user creates is readable/writable to *only* them *and* account A.


Thanks in advance for any/all help

---

### Post by HermanAB on 2007-07-18
1. See the 'users' directive in 'man smb.conf'.
2. 755 should work

See this: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by Darth_tater on 2007-07-18
> **HermanAB said:**
> 1. See the 'users' directive in 'man smb.conf'.
2. 755 should work

See this: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman



i will try out that create mask (thanks for that.. i never understood the users thingy in *nix) but i dont think you understood my first question.  what i meant is this:


/public/ ---- this is what is being shared across the network.
          |
          |
         +/all users/ ----- this is a global folder that all users need access to.
          |               |
          |               file.ext
          |
          |
         +/users A C and E */  ----this directory should only be visible to certain users; some shouldn't know it exists
          |                             |
          |                               private_file.ext
          |
         +/another dir/

*NOT user B or D, only user A C and E can see this directory when they open the /public/ directory


see, in this example, the /public/ share is a single service so the users directive is useless because that works per service and i need to set *two* sets of access rules per this *one service*

---

### Post by DaiLaughing on 2007-07-19
Disclaimer: I've set Samba up once (well three times but it only worked the last time) so if I'm missing the point be nice to me;-)

in /etc/samba/smb.conf you have to set up the shares.  One of mine looks like this:

path=/srv/home/stephen
writeable=yes
browseable=yes
valid users=stephen martin
admin users = debian martin
vfs object=recycle
recycle:repository=Recycle Bin
recycle:keeptree = No
recycle:versions=Yes

So my son and I can access his files but no one else in the family.  Is that what you wanted for question 1?

---

### Post by Darth_tater on 2007-07-19
not quite.  i know how to do what you are describing above, but that works per initial shared directory.

what i need is a way to share a single folder.  For example this is a TV folder... so that i can share all the things i have recorded with myth tv.  


so inside this TV folder there is a FAMILY folder which has shows for the kids and a few adult shows that are safe for kids too.  but also inside of this TV folder is another folder called ADULTS  which has things that are not ok for kids (think stuff like the soprano's) 


the TV folder is password protected, so that way anybody who needs to access it must login.  what i want is so that if you are *not* logged in as PARENTS (fore example) you cant see the other folder called ADULTS.  so when kids go to this folder to watch some TV they are *only* allowed to see the FAMILY folder.


hope that cleared it up.

---

### Post by DaiLaughing on 2007-07-19
Yes, sorry, should have realised.

I would say make users belong to different groups and then set permissions so that only your group can get at the folders you want kept private.  Then the parent public folder can still have read permission for "others".

---

### Post by Darth_tater on 2007-07-19
> **DaiLaughing said:**
> Yes, sorry, should have realised.

dont worry about it.  i guess ill have to think of something else.  

does smb.conf support simple logic statments?

like

IF user(!jimbob){

path=/home/public/
veto files = /notforkids_directory/*.*

else  

path=/home/public/ 
}

---

