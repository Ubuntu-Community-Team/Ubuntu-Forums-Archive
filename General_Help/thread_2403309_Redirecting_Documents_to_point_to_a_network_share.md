---
title: "Redirecting Documents to point to a network share"
date: 2018-10-10
forum: General Help
---

### Post by zenu2 on 2018-10-10
Hello Ubuntu forums:

i would like to redirect my Documents folder under my user profile to a network share. So the idea being when i open my Documents folder its actually opening a network share folder. 


My configuration:
- Ubuntu 18.04
- i am able to browse to the network share i want to redirect to, confirmed credentials

any guidance is appreciated.

---

### Post by jerome1232 on 2018-10-10
Assuming that this network share is always accessible, I'd use an fstab entry and mount the network share at ~/Documents.

Assuming the share is a windows/samba share, perhaps this document will help. The documentation looks old, but from some brief poking around, I think it's still relevant. 
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

If you are using some other type of share, or if you are still unsure of what to do, ask, I'm sure I can figure out some more specific guidance.

---

### Post by zenu2 on 2018-10-12
@jerome1232, thank you for the article. While it did work, what I am experiencing now is whenever another user logs in, that user gets the mapping defined in /etc/fstab. that makes sense based on design of the technology. 

what i am trying to do is map/redirect a home drive/personal drive for a logged in user to point to a NAS file share, specifically pointing Documents to a file share. This redirect would be based on user account, pointing each user to specific home drives hosted on a NAS. i would like to maintain secuirty, preventing other users from seeing/mapping another users home drive on the NAS files share.

a little more about what i have setup in my house:
- all file shares are on a NAS, running SAMBA and Windows CIFS services 
- im running zentyal ([http://www.zentyal.org](http://www.zentyal.org)) for various services, and have created a Domain via Zentyal's Domain and Directory services
- i registered my Ubuntu workstation to the Zentyal created Domain, and logging into my workstations via domain account hosted on Zentyal. Basically im running a opensource Windows Domain 

The idea being, when a user logs in i would map that users home drive to the NAS and redirect the Documents folder to the NAS file share. 

any recommendations?

---

### Post by jerome1232 on 2018-10-12
I'm sure there's a fancy solution with the domain and directory services. But that's out past my expertise. 

Me? I'd do something simple.

I'd make fstab entries for each user (my imaginary fstab entries using guest account to auth, your real fstab entries will naturally vary with the options you are using) and have different shares for each users Documents folder. As for maintaining security, that's out past what I know just off the top of my head. It would take some research on my part and unfortunately I don't have the time for that atm.

```

//server/user1    /home/user1/Documents   cifs   guest,uid=user1,iocharset=utf8   0 0
//server/user2    /home/user2/Documents   cifs   guest,uid=user2,iocharset=utf8   0 0
//server/user3    /home/user3/Documents   cifs   guest,uid=user3,iocharset=utf8   0 0

```

---

### Post by SeijiSensei on 2018-10-12
If you can set up the NAS to use NFS as well as CIFS, these things are much easier.

The Documents folder on all my desktops are symbolic links to my Documents folder on my NFS server.  You can't do that with CIFS because symlinks are not supported.

---

