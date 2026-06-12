---
title: "MLdonkey Incoming Path directory change?"
date: 2007-05-17
forum: General Help
---

### Post by antis0cial on 2007-05-17
Hi,

I have recently installed MLdonkey--server mldonkey--gui. All is working fine, the only complaint I have is that I cannot seem to change the location of the INCOMMING directory. 

The temp directory plays nice and is set to /TEMP/Downloads/TMP. I did this by editing the downloads.ini file and it was fine. Its just that there is no section for setting the incoming directory in the downloads.ini PATHS or in the GUI settings.

I tried copying and pasting the following into downloads.ini

(* The directory where downloaded files
  should be moved after commit *)
 incoming_directory = "/TEMP/Downloads/INCOMING"

But the above still didnt work. Its annoying coz the default location is limited in storage where as /TEMP is mounted to a 250GB download drive.

If anyone could help me that would be great as this has been doing my head in Linux aswell as Windows before when I tried MLdonkey. Or if someone could refer a different P2P app which uses ed2K aswell as Torrent support.

Thank you in advance, and please be aware that I am new to this Ubuntu / Linux. But have chucked out Windows and sticking to Linux from now on. Vista was too much of a dissapointment for me to stick around.

PS. I did use the following link as a guide; [http://www.trekweb.com/~jasonb/articles/mldonkey_linux.shtml](http://www.trekweb.com/~jasonb/articles/mldonkey_linux.shtml)


antis0cial

---

### Post by glauco.b on 2008-02-17
Ok, this is a very old post, but anyway... I have the solution so why not leave it for anyone having the same problem

The solution is quite easy.

Shut down the mldonkey server, edit the file downloads.ini (it's in the mldonkey config folder)

Scroll down to find the shared folders list and change the directives to whatever you need. What says to mldonkey if the folder is the "incoming" one is the sharing strategy. If you give a folder the "incoming_files" strategy, that will be your incoming folder

See my current config for example

```


shared_directories = [
  {     dirname = "/mldonkey/shared"
     strategy = all_files
     priority = 0
};
  {     dirname = "/mldonkey/incoming/files"
     strategy = incoming_files
     priority = 0
};
  {     dirname = "/mldonkey/incoming/directories"
     strategy = incoming_directories



```

---

