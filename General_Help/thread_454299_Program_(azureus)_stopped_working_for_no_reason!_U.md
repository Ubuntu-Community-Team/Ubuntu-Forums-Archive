---
title: "Program (azureus) stopped working for no reason! Ubuntu slowly dissapointing me...."
date: 2007-05-25
forum: General Help
---

### Post by moljac024 on 2007-05-25
I've been very enthusiastic about ubuntu (and linux in general), which i have installed a few days ago.
Now, i've heard about linux's general safety and stability (which is supposed to be higher than MS Windows's) and as much as i would love to believe that, Ubuntu keeps trying to convince me otherwise with constantly freezing my computer! (in the last few days my computer froze more times than it ever did with Windows XP)
I am getting disappointed.....

The newest surprise ubuntu gave me is that azureus suddenly stopped working. I installed it with synaptic and i tried reinstalling it with synaptic, i tried removing it with synaptic and installing it again, then i tried completely removing it and installing it again. Nothing, the same error and it won't start...

This is what i get in the terminal when i try to run it :

DEBUG::Fri May 25 16:25:47 GMT+02:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
DEBUG::Fri May 25 16:25:47 GMT+02:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
Aborted (core dumped)


I would like to note that my system froze when i tried running a game called vegastrike (i got it with synaptic) and that's when this started happening.
Did the freeze damage my system ? Please respond...thank you!

---

### Post by SteveHillier on 2007-05-25
Can I tentatively suggest that if you are getting progressively more system crashes that it might be hardware?
failing components on video cards, motherboards etc can fail intermittently and progressively
Steve

---

### Post by FunnyLookinHat on 2007-05-25
I had a similiar problem and was able to fix it by replacing the .jar file on my system with a new one from azureus.sf.net

If you are fairly comfortable with the command line, you can do this too...

I downloaded the latest .tar.bz2 file from:
[http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus_2.5.0.4_linux.tar.bz2&use_mirror=internap](http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus_2.5.0.4_linux.tar.bz2&use_mirror=internap)

Save it to your desktop for simplicity sake...
Once it has downloaded, go ahead and open it up and extract the files...

You will notice that one of the files you extracted will show up in a folder called azureus and will be called Azureus2.jar  This is the file we need to replace on our system.

Open up a terminal and run this command:
locate Azureus2.jar
If you don't get any results run "sudo updatedb" and then rerun the locate command.

Now navigate in your terminal to where you extracted the files from the downloaded .tar.bz2...  if you downloaded and extracted the files to your desktop you will probably do this:
cd Desktop
cd azureus

Now, look up at your locate command results...  see the exact path to the Azureus2.jar file on your system?  we're going to copy over our new file to that location...  For demonstrations sake, I'm going to say the path to the file is /path/to/Azureus2.jar bu this obviously won't be what your system has.

Do this command:
sudo mv Azureus2.jar /path/to/Azureus2.jar

And now you should be good to go.  You can delete the files and folders you saved and extracted to your desktop as well.  HOpe that helps.

---

### Post by moljac024 on 2007-05-25
Thanks for the help! I didn't do all those things, I removed azureus with synaptic and just extracted the contents of the .tar.bz2 in my /usr/bin/azureus and it works now!

> **SteveHillier said:**
> Can I tentatively suggest that if you are getting progressively more system crashes that it might be hardware?
failing components on video cards, motherboards etc can fail intermittently and progressively
Steve

There is nothing wrong with any of my hardware, but i think that my video card is the main source of problems (the other system freezes i had were because of beryl). I am using the open-source ati drivers that come with ubuntu as i was led to believe (by dozens of people) that the official ATI drivers are not worth installing...

---

