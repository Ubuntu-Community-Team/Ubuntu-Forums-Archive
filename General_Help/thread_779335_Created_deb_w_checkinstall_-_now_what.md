---
title: "Created deb w/ checkinstall - now what?"
date: 2008-05-02
forum: General Help
---

### Post by drs305 on 2008-05-02
What can I delete?

The latest version of audacity (1.3.4beta) doesn't have the tempo feature so I compiled the program and successfully got the tempo feature to work. Next I decided to try checkinstall and created a deb file after renaming the unzipped source folder audacity-src-1.3.4 (deleting the 'beta' tag). It appears to work and was created inside the installation folder.

The deb file (audacity-src-1.3.4-1_i386.deb) is located within the extracted source folder and now the program appears in synaptic as 'audacity-src'. The deb file's size is 1.7MB.

Can I save the deb file to another location and delete the original extracted source folder? Must I keep the dev files I downloaded to originally compile audacity? Would I need to reload all the dev files if I used this deb file to install this version of audacity later?

Since this app is listed as audacity-src in synaptic, can I also install the repository version of audacity (audacity 1.3.4-1.1ubuntu1 ? (I used sudo make install and later sudo checkinstall to install my compiled version).

Thanks.

For those interested in getting the tempo feature to work in linux, I mostly followed the instructions by ArtInvent here:
[http://ubuntuforums.org/showthread.php?t=684813](http://ubuntuforums.org/showthread.php?t=684813)
and this:
[http://audacityteam.org/wiki/index.php?title=Developing_On_Linux](http://audacityteam.org/wiki/index.php?title=Developing_On_Linux)

---

### Post by Grishka on 2008-05-02
> **drs305 said:**
> What can I delete?

The latest version of audacity (1.3.4beta) doesn't have the tempo feature so I compiled the program and successfully got the tempo feature to work. Next I decided to try checkinstall and created a deb file after renaming the unzipped source folder audacity-src-1.3.4 (deleting the 'beta' tag). It appears to work and was created inside the installation folder.

The deb file (audacity-src-1.3.4-1_i386.deb) is located within the extracted source folder and now the program appears in synaptic as 'audacity-src'. The deb file's size is 1.7MB.

Can I save the deb file to another location and delete the original extracted source folder? Must I keep the dev files I downloaded to originally compile audacity? Would I need to reload all the dev files if I used this deb file to install this version of audacity later?

Since this app is listed as audacity-src in synaptic, can I also install the repository version of audacity (audacity 1.3.4-1.1ubuntu1 ? (I used sudo make install and later sudo checkinstall to install my compiled version).

Thanks.

For those interested in getting the tempo feature to work in linux, I mostly followed the instructions by ArtInvent here:
[http://ubuntuforums.org/showthread.php?t=684813](http://ubuntuforums.org/showthread.php?t=684813)
and this:
[http://audacityteam.org/wiki/index.php?title=Developing_On_Linux](http://audacityteam.org/wiki/index.php?title=Developing_On_Linux)

you can copy .deb file anywhere and remove the source folders. you won't need the development libraries to run it, they are only needed during compilation. you will, however, need the user versions of corresponding libraries. you probably could install audacity from the repos as well, as checkinstall usually puts installed files in /usr/local/ subfolders, and software installed from official repos ends up in /usr/ subfolders. though there's no guarantee it'll work well.

---

