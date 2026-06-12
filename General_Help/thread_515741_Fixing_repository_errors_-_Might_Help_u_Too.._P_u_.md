---
title: "Fixing repository errors - Might Help u Too.. :P u know those update ones..."
date: 2007-08-02
forum: General Help
---

### Post by nowshining on 2007-08-02
well I have been having some problems if nothing else works try this that also seems to work for me and maybe for u.:

1st purge the Update/install cache

open up a terminal and type or copy + paste
apt-get remove --purge
open up Sofware Sources - Uncheck the ones checked and re-check them

Then go to the tab that says  update and uncheck and re-check the boxes, that you had checked before:

Next to to the Tab Authentication and click the Restore Defaults Button... 

*Note: Some repositories are known to send CheckSum Errors  in otherwords they are broken packages and these sources should be avoided.. U can Remove any that you have and only leave the defaults which Should also Solve Many people's problems, by going to the third party tab of software sources and delete everything in there by selecting it and hitting remove at the bottom.. This also Applies To the Authentication tab and By restoring the Defaults you lose any Manually input Authentication checksums...

Next before u do anything else go to login as as the root by doing the following (if anyone knows how to get to and delete the following in the folder mentioned from the users and non-root desktop session please post)...

anyway moving on, go to System - Administration - login Window
Input your password

Click The Tab that Says Security 

Find Allow Local Administrator login and check mark it.....

next press the quit button, select Switch User
Input root as the username and input the root password - hit enter or click Login/okay - whatever it says and however u login, next

Open up the Filesystem press ctrl + H to unhide the hidden files
then go to /var/lib/apt/lists/partial/ and delete everything in there..
In other words start in Filesystem then find the Var folder then in there find the lib folder then in there find the lists folder then in there find the partial folder and then your done except remove everyone of those files located in that folder..
 
close the Window, Press the Quit BUtton and log out.

Now u'll be re-asked to login to ur user accound if u do not see anything but a black background move ur mouse or hit a key, then type in ur password and hit okay, go back into login window and un-check allow local system administrator login press close...


sources: 
[http://www.webservertalk.com/archive291-2006-2-1394937.html](http://www.webservertalk.com/archive291-2006-2-1394937.html)
Automatrix or whatever forum from somebody that I believe also frequents this forum, This forum in Fragmented Posts, etc...

---

