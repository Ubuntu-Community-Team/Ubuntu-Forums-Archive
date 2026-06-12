---
title: "trouble installing Samba server"
date: 2005-05-02
forum: General Help
---

### Post by young on 2005-05-02
Hi there,

      I am having a bit of trouble installing Samba server.  When I type in 

  ```
sudo apt-get install samba
```

    I get the following message: Sub- process /usr/bin/dpkg returned an error code (1)


   Does anybody know how to fix this problem?  Your help will be more than  
   appreciated.  Thank you in advance.


                                                                                                    Cheers,

                                                                                                                       Young

---

### Post by nemin on 2005-05-02
[QUOTE=young]
      I am having a bit of trouble installing Samba server.  When I type in 

  ```
sudo apt-get install samba
```

    I get the following message: Sub- process /usr/bin/dpkg returned an error code (1)
[/QUOTE]
Are you very sure that's the only error message you get? Has apt-get ever worked correctly (with other packages)?

---

### Post by young on 2005-05-02
Hello nemin,


                  Thank you for your reply. Yes, apt-get pretty much worked for almost 
       everything, including mysql package.  


                    Just to make everything more clear, I decided to run the same command
     again, and this is what I get:

      ```

      Reading Package Lists... Done
      Building Dependency Tree... Done
      samba is already the newest version.
       0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.
      1 not fully installed or removed.
      Need to get 0B of archives.
     After unpacking 0B of additional disk space will be used.
     Setting up samba (3.0.7-1ubuntu6.3) ...
     update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba
     update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba
     invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
     dpkg: error processing samba (--configure):
     subprocess post-installation script returned error exit status 102
     Errors were encountered while processing:
     samba
     E: Sub-process /usr/bin/dpkg returned an error code (1)
```

     Thank you for reminding me to post the details. My appologies for being lazy.

                                                                                                                       Young

---

### Post by nemin on 2005-05-07
[QUOTE=young]
                  Thank you for your reply. Yes, apt-get pretty much worked for almost 
       everything, including mysql package.  


                    Just to make everything more clear, I decided to run the same command
     again, and this is what I get:

      ```

      Reading Package Lists... Done
      Building Dependency Tree... Done
      samba is already the newest version.
       0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.
      1 not fully installed or removed.
      Need to get 0B of archives.
     After unpacking 0B of additional disk space will be used.
     Setting up samba (3.0.7-1ubuntu6.3) ...
     update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba
     update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba
     invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
     dpkg: error processing samba (--configure):
     subprocess post-installation script returned error exit status 102
     Errors were encountered while processing:
     samba
     E: Sub-process /usr/bin/dpkg returned an error code (1)
```
[/QUOTE]
Hmm, that looks strange to me :-? I'd advise to first remove samba completly, with apt-get remove samba, and then install it again. No idea what to do else ](*,)

---

### Post by young on 2005-05-07
Hi there,

        Thank you for your reply.  I actually solved the problem.   I can't quite remember
    the exact details of how I did it, but I will post it up as soon as I remember.

                                                                                                Regards,

                                                                                                                   Young

---

