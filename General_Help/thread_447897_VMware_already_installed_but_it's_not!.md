---
title: "VMware already installed? but it's not!"
date: 2007-05-18
forum: General Help
---

### Post by Nibblet909!! on 2007-05-18
hey, im trying to install vmware server through the repo's, but im getting this messege 


Package configuration                                                           
                                                                                
                                                                                
                                                                                
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring vmware-server &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; A previous installation of a VMware product has been detected.            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you installed it from the VMware website, please remove it by running  &#9474;  
 &#9474; vmware-uninstall.pl before proceeding.                                    &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If it was installed through Ubuntu, you must purge (completely remove)    &#9474;  
 &#9474; the old package.                                                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                                                
                                                                                
     I did install vmware-player through automatix, but i uninstalled it too. i;ve also tried to purge all the files, and it seemed to work, but i got the same messege. i stil have all the deb's in my /apt/archives folder, but i can't delete them. i also completly removed vmware player through Synaptic, but that didn't work either.     help would be appreciated! :confused::(

---

### Post by veloce on 2007-05-19
VMWare Player leaves a directory on your system somewhere.  From what I've seen when others have asked the same question here, I think its in the /etc directory. 

Otherwise do a search for vmware with:

sudo gnome-search-tool

---

### Post by Nibblet909!! on 2007-05-20
thanks! but, i deleted it and i still get the same messege...:(

---

### Post by veloce on 2007-05-20
> **Nibblet909!! said:**
> thanks! but, i deleted it and i still get the same messege...:(

So there is nothing on your system with a name including vmware anymore?

Any you've restarted?

If so, this one is beyond me.  There shouldn't be anything else vmware related left on the system as far as I know.

---

### Post by dpj23 on 2007-05-20
You will have to re-install vmware product to get it back working again...

This may need you to re-install manually from the command prompt...

In cases such as this I repair by logging in as root and then starting install process...

---

### Post by zvacet on 2007-05-21
Look if you have vmware folder in **etc**.if you have delete it.

---

