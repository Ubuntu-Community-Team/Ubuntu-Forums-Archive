---
title: "package installation problem"
date: 2007-03-03
forum: General Help
---

### Post by da_bomb on 2007-03-03
I am quite new to linux/ubuntu and have run into some difficulty. Any help would be GREATLY appreactiated as i have lost all hope

i successfully used the synaptic package manager to install apache2/php5/mysql + some extra php5 modules here and there.........everything was working absolutely fine until i ran accross a package called "myphpmoney" and decided "well i might as well give it a go" and clicked to install it" - BIG MISTAKE

it downloaded the program but also put php4 on my system with a few php4 modules. now my webserver runs php4 which i really dont want - i cant get pack to php5 because there is something messed up with the myphpmoney uninstallation - any combination of uninstalling either apache totally, or php4 or reinstalling php5 requires the removal of myphpmoney. 

basically whenever it tries to remove this proggie it gets stuck and gives me this message:
Removing myphpmoney....
* Forcing reload of apache 2.0 web server....
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
OK


it just sits there and i have to interrupt the process cause it just doesnt do anything - i cant reinstall apache....or php5 or remove php4 cause they all tell me that part of that involves removing this program - i fear its completely messed up the entire tracking of packages and config files - like i said i am a beginner so i dont really know whats going on in terms of config files and stuff in the background of this package manager. The worst thing is that although the manager says the package is installed, the folder is no longer in the webroot - so its kind of registered as installed but not really there?!?

perhaps some sort of way of aborting that part of removal without ending the rest - at the moment when i press ctrl+c it aborts trying to uninstall myphpmoney, but then it doesnt carry on to try and install other packages 

any help would be GREATLY appreciated - THANKS IN ADVANCE

---

### Post by disturbedite on 2007-03-03
someone may want to suggest a different approach, but if you can't resolve it any other way, i'd recommend seeing my post [here]("http://kubuntuforums.net/forums/index.php?topic=13297.msg53029#msg53029").

your circumstances are a bit different, but the action i suggested there could work here too, i think.

---

### Post by da_bomb on 2007-03-03
THANK-YOU VERY MUCH DISTURBEDITE 

THAT FIXED THE PROBLEM - by hiding myphpmoney from the manager i was able to remove all apache and php packages totally, and then fresh install apache2 and php5 

THANKS  :)

---

### Post by disturbedite on 2007-03-03
no prob!  thats what the forum is for.  glad i could help.:guitar:

---

