---
title: "what is proper location"
date: 2012-11-02
forum: General Help
---

### Post by workaround on 2012-11-02
I need to install this: "install_flash_player_11_linux_x86_64.tar.gz"
This text below came from the text file provided by adobe.
-------------------->>
Installing using the plugin tar.gz:
    o Unpack the plugin tar.gz and copy the files to the appropriate location.  
    o Save the plugin tar.gz locally and note the location the file was saved to.
    o Launch terminal and change directories to the location the file was saved to.
    o Unpack the tar.gz file.  Once unpacked you will see the following:
        + libflashplayer.so
        + /usr
    o Identify the location of the browser plugins directory, based on your Linux distribution and Firefox version
    o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
        + cp libflashlayer.so <BrowserPluginsLocation>
    o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
        + sudo cp -r usr/* /usr
-------------------->>
What is: "... appropriate location..."? // first bullet
where would be: "... libflashlayer.so <BrowserPluginsLocation>..."? // sixth bullet
Thanks.

---

### Post by Abhinav Kumar on 2012-11-02
Appropriate location could be any folder of your choice say 

~/Desktop/

Folder location in which .so file should be copied is 

/usr/lib/mozilla/plugins/

You can type ```
ls /usr/lib/mozilla/plugins/
```
and there will be some .so files
:)

---

