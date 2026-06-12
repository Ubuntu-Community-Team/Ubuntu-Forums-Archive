---
title: "Why my php app under docker failed failed Google verification ?"
date: 2023-08-18
forum: General Help
---

### Post by nilovsergey on 2023-08-18
I changed my job and in my working browser google-chrome 114.0.5735.90-1 (under home kubuntu 20.04) set up a google account
(I connect to many external apps/services through it)

And launching the application url [http://127.0.0.1:8081/auth](http://127.0.0.1:8081/auth) (this is the hosting of the application launched under docker/php/apache2)
I get an error
> Access blocked: App "myapp name app" failed Google verification

[EMAIL="myname@mycompany.com"]myname@mycompany.com[/EMAIL]
The app "myapp name app" has not been verified by Google yet. Until the process is completed, the application is only available to testers approved by the developer.
If you think you should have access to it, please contact the developer.
If you are the developer of the "myapp name app" application, please see the details of the error.
Error 403: access_denied

Can you tell me what is this error and how to fit it?

I guess I can sign out of my google account - but I wouldn't want to
How can I remove this protection - I do not need it.
I didn't really understand where it came from - in my opinion after I installed and set up a new google account ...

Can it be controlled by some account console or by external plugins?

---

### Post by TheFu on 2023-08-18
> Error 403: access_denied

That's an HTTP error.  Check file permissions for the directories and files.  

If it is google providing the error, then you may need to wait for them to remove you from their abuse block list.  I'd guess your php webapp is the issue, however.  

I know next to nothing about docker, but when you setup the php webapp, the directory and file permissions need to allow the daemon running the webapp to have appropriate access to the files and directories.  On Ubuntu, apache typically runs a www-data user in the www-data group.  Other linuxen use different usernames/groups. For example, I think the redhat-based systems use the httpd account, but don't quote me on that.

---

