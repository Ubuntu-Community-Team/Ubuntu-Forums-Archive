---
title: "network search app"
date: 2005-06-06
forum: General Help
---

### Post by rjs on 2005-06-06
G'day all,

does anyone know a good app to search a local (windows) network. It would be nice to be able to search by name or file type. Thanks.

paz y amor,
-rjs.

---

### Post by lt_kije on 2005-06-06
I have no direct experience with this, but Simple Samba Commander seems to be the closest thing I can find; see [http://smbc.airm.net/](http://smbc.airm.net/).

I don't think this will do exactly what you're looking for (ie search across shares), but to do this, you'd need to do some indexing that is not part of the SMB protocol. Alternatively, if you mount each of your shares, you should be able to use the standard Unix 'find' command to search the remote filesystems.

HTH,
lt_kije

---

### Post by rjs on 2005-06-06
Well the network is about a thousand computers which (since they are all desktops/laptops) are continuesly joining and leaving the network, so is mounting them all a viable option (ie. is there someway to do it automagically, without making my very old laptop burst into flames)? Also, if i start downloading something from someone else's box, and they decide to turn it off before ive finished getting it all, is there someway of being able to automatically finish the download when they next join the network?

paz y amor,
-rjs.

---

### Post by lt_kije on 2005-06-06
Again, I don't think that the SMB protocol is really designed for what you want to do. Creating a distributed file system (eg AFS) or a local P2P network (Ant? MUTE?) might be more what you're looking for.

A large network of workstations is not an ideal file sharing environment. Mounting all of the hosts is probably not an option; neither, likely, is an auto-resume function (unless you code it yourself).

Can you describe your environment a bit more? Are all the hosts connected on a 100Mbit lan? Wireless? University?

HTH,

lt_kije

---

### Post by lakcaj on 2005-06-06
Nautilus should be able to see all your windows machines.  Open nautilus, and under "places" go to "computer" and then "network".  Or, you could just open nautilus as a file browser, and enter network:/// in the url field.

---

### Post by tread on 2005-06-06
If I remember correctly, there is a tool called Linneighborhood (check spell?) which you can use to browse and mount smb shares.

---

### Post by rjs on 2005-06-06
Its an 100mbit LAN in my university's residences (i think these are called colleges or something in america, anyway here down under we call them ressies). I have no problem using samba to browse the network, but since it is so huge it would be nice to be able to search it. There is some free (i dont know if thats gratis or libre) software that allows the windows computers on the network to search it, but that really isnt an option for me.

There is heaps of good stuff on it, but at the moment it's like straining sewrage with your teath (thanks to UF for that phrase).

paz y amor,
-rjs.

---

### Post by lt_kije on 2005-06-07
[QUOTE=rjs]Its an 100mbit LAN in my university's residences (i think these are called colleges or something in america, anyway here down under we call them ressies). I have no problem using samba to browse the network, but since it is so huge it would be nice to be able to search it. There is some free (i dont know if thats gratis or libre) software that allows the windows computers on the network to search it, but that really isnt an option for me.

There is heaps of good stuff on it, but at the moment it's like straining sewrage with your teath (thanks to UF for that phrase).

paz y amor,
-rjs.[/QUOTE]
 What's the windows utility called?

---

### Post by rjs on 2005-06-08
[ShareScan](http://www.sharescan.net/) (the website seems to be broken at the moment; [tucows](http://www.tucows.com/preview/220820))

paz y amor,
-rjs.

---

