---
title: "Browser Crashes -- Firefox and Seamonkey"
date: 2007-09-06
forum: General Help
---

### Post by brn on 2007-09-06
Compaq Presario 502 laptop: 1.8 GHz Celeron, 80 GB, 512 MB.  Dual boot Fiesty/Vista.

I have the lastest releases of* Firefox, Seamonkey*, and* Flashplaye*r.  Both of these browsers abruptly crash when loading a page that requires Flashplayer. (Example, [http://www.speakeasy.net/speedtest](http://www.speakeasy.net/speedtest) which I occasionally use  to check my DSL).  This does not happen with* Epiphany, Galeon*, or *Opera* (which for some reason checks only the download speed).  I also have *Konquero*r which loads the page (without crashing) but won't run the speed test.  Firefox did not have this problem before upgrading to the latest 2.x release.  I installed Seamonkey only a few days ago. 

the same thing is true for web forums that have "Flashchat" facilities.  I have installed a plugin recommended in this forum (URL?) which  will block Flashplayer operation for the purpose of disabling those annoying animations some web pages exhibit,  instead displaying a button which will enable it.  When the browser doesn't crash this works as advertised.  This morning I reinstalled Flashplayer with Synaptic Package Manager.  Suddenly everything worked just fine.  So I turned off the machine but found the problem was back just now when I restarted.  So I again reinstalled Flashplayer and once more both browsers work just fine with flashplayer.  I'm stumped.  Has anyone else experienced anything like this?  Will I have to reinstall flashplayer every time I restart the machine?.  

-Thanks-

I hate  just tested both browsers and found them OK.  Then I closed them and repeated the trial.  Both crashed.  So once more I reinstalled Flashplayer and both worked.  Then I closed and restarted the browsers and again they crashed.  I bet if I reinstall Flash yet again, this scenario will repeat indefinitely.  Very-very strange!

--Fixed--  Synaptic installs Flashplayer in /usr/lib/mozilla/plugins where it is found by most browsers but not in ~/.mozilla/plugins where firefox and Seamonkey look.

---

