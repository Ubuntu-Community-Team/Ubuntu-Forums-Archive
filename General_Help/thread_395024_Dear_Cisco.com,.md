---
title: "Dear Cisco.com,"
date: 2007-03-27
forum: General Help
---

### Post by diablo75 on 2007-03-27
This is a copy of a letter I sent to Cisco.com today.  There is a problem with their website, or something wrong with Ubuntu (I can't tell yet), and I wanted to let them know about it.  I also wanted to let you know about it, so this issue can be attacked from both sides.

Thanks for reading:
[FONT="Times New Roman"]
Hello.

I am currently a student of Cisco's online CCNA academy.  I also happen to use Ubuntu Linux and Firefox as my primary browser.  I've been using Ubuntu for about 2 or 3 months now, and I enjoy it and intend to migrate all my computer usage needs into it.

I have a problem with a particular link on your website.  When I go to log in to my account so I can access my curriculum, (at “cisco.netacad.net”)  I'll enter my username and password, and then am forwarded on to this address:

[http://cisco.netacad.net/cnams/public/Checker.jsp](http://cisco.netacad.net/cnams/public/Checker.jsp)

The web page displays nothing but a solid white background and no text, and essentially hangs the web page.

There is viewable source code as well:[/FONT]

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<!-- CNAMS 2.8 Enhancement | 041007-000279 Move Login Fields to Homepage | Author: Rakesh Nagar -->

<html>
<body>






  <script type="text/javascript" src="/cnams/public/Dispatcher.js"></script>
  <script language="VBScript" src="/cnams/public/Dispatcher.vbs"></script>
<form name="LoginFormNew" action="" method="post">
        <input value="/public/Login.jsp" type="hidden" name="ref">
        <input value="true" type="hidden" name="checkFlash">
        <input value="" type="hidden" name="flashCheckCode">
        <input value="LoginFormNew" type="hidden" name="formName">
        <input name="LoginUserSubmitNewEvent" type="hidden" value="Enter">

        <input name="userName" size="10" type="hidden" value="[COLOR="Red"]Edited out[/COLOR]">
        <input name="password" size="10" type="hidden" value="[COLOR="Red"]Edited out[/COLOR][/COLOR]">             

</form> 

        <script>
                    var flashCheckCode = MM_FlashDetect(
                    /*version of Flash software used to author content*/
                        6.0,
                    /*Boolean indicating whether to require latest revision of player (plug-in only)*/
                                true,                                   
                        /*Boolean indicating whether to install if player is not installed*/
                                !MM_FlashUserDemurred(),
                        /*Boolean indicating that the auto-installation should not occur and that the user will go to the installURL or to the upgradeURL as specified*/
                                true                                    
                        );
                        
                        /* flashCheckCode = 1: Required Version of Flash Plug-in is installed on user`s computer */
                        /* flashCheckCode = 2: Old Version of Flash Plug-in is installed on user`s computer */
                        /* flashCheckCode = 3: Flash Plug-in is NOT installed on user`s computer */

                if ("/public/index.html" != "/public/index.html") {
                        window.location = "/cnams/public/Login.jsp";
                } 
                else 
                {
                        document.LoginFormNew.flashCheckCode.value = flashCheckCode;
                        if( flashCheckCode == 1 ) {
                                document.LoginFormNew.action = "/cnams/dispatch";                               
                        }
                        else if( flashCheckCode == 2 ) {        
                                document.LoginFormNew.action = "/cnams/public/Login.jsp";
                        }
                        else if( flashCheckCode == 3 ) {
                                document.LoginFormNew.action = "/cnams/public/Login.jsp";
                        }
                        document.LoginFormNew.submit();
                }
                
        </script>


</body>
</html
-----------------------------------------------
[FONT="Times New Roman"]I have Flash as well as Java plugin's correctly installed, and testing their functionality has been done on many websites that use both.  I am not skilled enough to tell what is causing the page to hang, but I will be posing this question to the Ubuntu community forums to see if anyone out there might have a solution to this.  If I find one, I will happily check back in with you guys, and pass along what I learned.  I would also be glad to answer questions if I can provide feedback of another kind to develop a fix.

Thank you for your time.[/FONT]

---

### Post by m83 on 2007-03-27
I have the same problem. I complained to CISCO using their "Contacts & Feedback" page that using Firefox I couldn't login to [http://cisco.netacad.net](http://cisco.netacad.net). Their answer was to login using another URL: [http://cisco.netacad.net/cnams/dispatch](http://cisco.netacad.net/cnams/dispatch). This works, but I find it very unprofessional for CISCO that their site doesn't work with the number 2 browser in the world.

---

### Post by mark_g on 2007-03-27
It's probably Ubuntu related, because in Firefox in Windows and Slackware it works perfectly as someone stated in this thread not so long ago ( [http://www.ubuntuforums.org/showthread.php?t=366741](http://www.ubuntuforums.org/showthread.php?t=366741) ). 
Maybe Feisty will solve this problem...

---

### Post by amdalex on 2007-03-27
I tried the link with FireFox on windows and it works fine.

---

### Post by little jo on 2007-03-31
I think it's a problem of Linux Flash 9(or Cisco website doesn't recognize Linux Flash 9). I have a Debian, If I install Flash 7, log-in works, if I install Flash 9, it doesn't work.

---

### Post by little jo on 2007-04-07
Hello,
I found the solution...
It's a problem of flash 9 plugin. So, you have to set the flash 7 plugin in the firefox plugin directory (probably /usr/lib/firefox/plugins). Make attention change the name's file (e.g. libflashplayer7.so instead of libflashplayer.so because it's also the name of flash 9).
Thus :
$ sudo -s
# mv libflashplayer.so /usr/lib/firefox/plugins/libflashplayer7.so

However there is a problem : you're now with flash 7 plugin. 
So If want to change into version 9 :
# cd /usr/lib/firefox/plugins/
# mv libflashplayer7.so .. # for example
And switch off and on firefox

And if you want to surf in the CISCO Website:
# cd ..
# mv libflashplayer7.so plugins/
And switch off and on firefox

If you haven't flash 7 plugin,
you can download here:
[http://www.wikiupload.com/download_page.php?id=121059](http://www.wikiupload.com/download_page.php?id=121059)

---

### Post by Swab on 2007-04-07
I login at this URL: [http://cisco.netacad.net/cnams/public/Login.jsp](http://cisco.netacad.net/cnams/public/Login.jsp)

---

### Post by little jo on 2007-04-07
Oh thanks it's easier... :)

---

