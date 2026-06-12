---
title: "wierd issue. possible adware?"
date: 2012-10-27
forum: General Help
---

### Post by metalgs78 on 2012-10-27
1     down vote          [favorite]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#")            
                                     Recently i have noticed when browsing a web page will be  redirected to something other than what i click on. For instance, when i  tried going to [www.askubuntu.com](www.askubuntu.com) via a link on ubuntu.com it redirected  me to some other site than this one.
  Also when on a page with no flash videos of any kind or pop up  windows an ad will start playing. The only way to get it to stop is to  wait for it to finish or close the browser and start over again. I have  run Clam AV but it has not found anything.
      
                          [antivirus]("http://askubuntu.com/questions/tagged/antivirus") [malware]("http://askubuntu.com/questions/tagged/malware")      
                         [share]("http://askubuntu.com/q/207199/101358")[edit]("http://askubuntu.com/posts/207199/edit")[flag]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#")
                                                       edited                              [1 hour ago]("http://askubuntu.com/posts/207199/revisions")          
                      [URL="http://askubuntu.com/users/2022/cprofitt"][IMG]http://www.gravatar.com/avatar/78b934fb1c05b722ef6c20dc76cc76da?s=32&d=identicon&r=PG[/IMG]
[/URL]         
                      [cprofitt]("http://askubuntu.com/users/2022/cprofitt")
            3,069626         
     
                                                                   asked  2 hours ago         
                      [URL="http://askubuntu.com/users/101358/tim"][IMG]http://www.gravatar.com/avatar/6f227ab3f0edda12471c95df517b8e91?s=32&d=identicon&r=PG[/IMG]
[/URL]         
                      [Tim]("http://askubuntu.com/users/101358/tim")
            61         
     
                 
         
                                                   1               Could it be that something has been changed to your DNS, or someone has been fscking around in your /etc/hosts file? – [Nanne]("http://askubuntu.com/users/11120/nanne") [2 hours ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257539_207199")
                                
        I am a  newbie to ubuntu. I know what a host file but not sure where to find it  in Linux to check. I am the only user of this laptop and i know i  haven't. – [Tim]("http://askubuntu.com/users/101358/tim") [1 hour ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257554_207199") 
                                
        Well, you could type something like less /etc/hosts in a console, and see if something funky is going on there. You might for good measure do the same with /etc/resolv.conf – [Nanne]("http://askubuntu.com/users/11120/nanne") [1 hour ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257565_207199")
                                
        @Tim - is this while you are on Ubuntu or are you also running Windows on the machine? – [cprofitt]("http://askubuntu.com/users/2022/cprofitt") [1 hour ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257569_207199")
                                
        the  host file looks normal. It has the standard 1270.0.1 in there but  nothing else. The other one shows nothing out of the ordinary either. – [Tim]("http://askubuntu.com/users/101358/tim") [1 hour ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257570_207199") 
                                
        @cprofitt in ubuntu not in a windows. Windows is not running on this machine. – [Tim]("http://askubuntu.com/users/101358/tim") [1 hour ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257571_207199") 
                                
        Odd -- I  have heard of malware that does that in Windows, but not OS X or Linux.  The music / ads playing in the background makes this interesting. I was  hoping you were running Windows in a VM or Ubuntu in a VM because then  the issue might have been easier to fix. – [cprofitt]("http://askubuntu.com/users/2022/cprofitt") [1 hour ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257572_207199")
                                
        my thoughts exactly. – [Tim]("http://askubuntu.com/users/101358/tim") [1 hour ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257573_207199") 
                                
        @Tim -- you might want to run a rootkit detector. [rootkit.nl/projects/rootkit_hunter.html]("http://www.rootkit.nl/projects/rootkit_hunter.html") – [cprofitt]("http://askubuntu.com/users/2022/cprofitt") [1 hour ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257578_207199")
                                
        I tried  looking up how to install from a tar.gz but  it is not working. i typed  in "tar zxvf rkhunter-1.4.0.tar.gz" but i keep getting errors and it  won't do it. do i have to be a root user? – [Tim]("http://askubuntu.com/users/101358/tim") [56 mins ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257592_207199") 
                                
        @Tim sudo apt-get install rkhunter – [cprofitt]("http://askubuntu.com/users/2022/cprofitt") [34 mins ago]("http://askubuntu.com/questions/207199/browsing-redirected-and-ad-playing-in-background-malware#comment257598_207199")





I posted this on askubuntu.com and i was told to post this here I'm hoping we can get this resolved. Please read through and let me know your thoughts on this. I have done the last hting i was told to do but where do i go to start the rootkit scan?

---

### Post by westie457 on 2012-10-27
A lot of sites these days use 'pop-under' advertising. Clicking anywhere on the page will usually open another window to an outside site. I think they do this to generate revenue for themselves and the site you are re-directed to. Pop-up links are easier to block than pop-under ones.

Not of any technical help to you, just general advice of observations in my own surfing habits.


Try 'chkrootkit' it is in the repo's

---

