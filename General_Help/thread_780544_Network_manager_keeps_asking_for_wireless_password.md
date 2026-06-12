---
title: "Network manager keeps asking for wireless password (not keyring passwd)"
date: 2008-05-03
forum: General Help
---

### Post by guano on 2008-05-03
Hi all. Running Hardy here, with base install (Gnome) and using XFCE as WM. My problem is that network manager keeps asking for the password to connect to my wireless router, instead of just asking for default keyring at the session startup and then not asking anymore.
That is, keyring is not doing its job.
any ideas?

tks

---

### Post by ade90212 on 2008-05-03
A workaround for this is to dispense with network manager and use Wicd instead. Wicd is a better Wi-Fi manager and it doesn't require that you enter your default keyring password at start-up.

See [this link]("http://wicd.sourceforge.net/download.php") for details on downloading and installing.

---

### Post by guano on 2008-05-05
Thanks for the tip. Wicd is working fine.

---

### Post by johnmc on 2008-05-08
I'm having the same problem - eventhough network manager is allowed to access keyring it keeps asking for the password...
Switching to another application isn't the solution though (in terms of solving the problem with network manager...)
So if anyone got any idea please share! Thanks.

---

### Post by danwood76 on 2008-05-08
Have you tried deleting all the wireless networks contained in the wireless networks manager and re saving the passwords?

I have had no real issues with the new network manager, it seems a lot better at just loading up my wifi networks and not moaning about passwords.
Though I changed my wifi password once when I defaulted the settings on my router and even though I reconfigured it back to the original it was doing what you are describing here.
After deleting the wireless networks from the list and re doing it they work again.

---

### Post by repseki on 2009-05-19
> **danwood76 said:**
> Have you tried deleting all the wireless networks contained in the wireless networks manager and re saving the passwords?

I have had no real issues with the new network manager, it seems a lot better at just loading up my wifi networks and not moaning about passwords.
Though I changed my wifi password once when I defaulted the settings on my router and even though I reconfigured it back to the original it was doing what you are describing here.
After deleting the wireless networks from the list and re doing it they work again.
thank you, this worked for me.

---

### Post by Beast14 on 2010-05-07
Hi, 

I actually have found the solution to this problem. Currently i have Ubuntu 9.10 Karmic Koala and Ive been having problems with the wirless too. it works perfect with the network manager, just sometimes it will just suddenly lose its wireless connectivity and continously ask me for my wpa2 key..i restarted pc and everything was fine when i logged back in.
It seems like its having some permissions issue.

it did this again after a couple of hours and then i looked in my processes, i killed 'NetworkManager'
'modem-manager' and
'wpa-supplicant'

using **sudo** kill [psID] 

anyway, after i did that, it restarted my wireless afresh and kept my password this time. this might be a bug on the new ubuntu with user permissions. but this is just a temporary solution.

hope this helps!!:p

---

### Post by garvinrick4 on 2010-05-07
Keyrings  
 

    1. Open up your Home Folder by clicking Places>Home Folder  
    2. Press CTRL-H (or click View>Show Hidden Files)  
    3. Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it  
    4. In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.  
    5. Delete any files you find within the keyrings folder  
    6. Restart the computer  
 

 After you restart and login (if you’re automatically logging in) you’ll probably be asked to enter your wireless networks WPA/WEP encryption key.  After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password and lock it away with a new keyring password.  The box looks like this:  
 

 Instead of typing in a new password, leave both boxes completely empty and click Create.  
 

 You’ll then be asked if you know what the hell you’re doing:  
 

 Go ahead and click Use Unsafe Storage.  
 

 WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT and not in an encrypted form.  So it is imperative that you are certain no untrustworthy persons can access your user account (either physically or by remote) or they will be able to easily open and read this file and obtain many passwords (for things such as FTP accounts, SSH, e-mail accounts, etc).  Proceed with caution.  
 

 From here on all keyring stored passwords you enter will not safeguarded behind a master password or encryption.  Whether or not you want to do this is entirely up to you.  I personally have had enough of the keyring manager and consider it kind of annoying.  But as I said before, you may have certain environmental factors that make having a master password over the rest of your passwords a good idea.  Keep in mind that the keyring password manager has absolutely nothing to do with your administrative/root privilages password that has to be entered any time you want to apply updates, or add/remove software.  You will still have to type your account password in for these actions, and that is something I am quite comfortable with.

---

### Post by the8thstar on 2010-08-14
I have tried all the above methods to no avail. Ubuntu keeps asking for the wireless pasword every time I reboot my computer. Is there a solution for this?

---

### Post by SirGonzo420 on 2011-07-28
Sorry to bump such an old thread but apparently, this is still a problem.


Any working solutions?

---

### Post by Dennis N on 2011-07-29
You might try this. It fixed this problem for me (11.04):

Right click on network manager icon and choose 'edit connections'. Under the wireless tab, select your network connection, and then press the edit button. Check the box at the bottom which says (or something like) "make available to all users" (it was initially unchecked). 

Next time you log in it should be fixed.

---

### Post by SirGonzo420 on 2011-07-31
> **Dennis N said:**
> You might try this. It fixed this problem for me (11.04):

Right click on network manager icon and choose 'edit connections'. Under the wireless tab, select your network connection, and then press the edit button. Check the box at the bottom which says (or something like) "make available to all users" (it was initially unchecked). 

Next time you log in it should be fixed.

Thanks, I tried that, but still no luck. :(

---

### Post by northd_tech on 2011-08-26
> **SirGonzo420 said:**
> Sorry to bump such an old thread but apparently, this is still a problem.

Any working solutions?

I'm not sure what architecture, Ubuntu version, or hardware you are running.  I have recently found that running Updates will apparently re-install [Gnome] Network Manager, and it does not like to "play nice" with the Wicd WiFi manager (although it had worked for months for me having **both** installed earlier this year under 64-bit Ubuntu Lucid Lynx 10.04.2 LTS).

If you want to review the Wicd/Network Manager conflict, post #5 on this thread is a good, recent place to start:

[http://ubuntuforums.org/showthread.php?t=1675398](http://ubuntuforums.org/showthread.php?t=1675398)

---

### Post by s.m.knipe on 2012-04-27
Bump

I am also having this wifi network password issue after upgrading to 12.04 LTS (was perfect on 11.10), and nothing I have found in searches thus far has helped...

---

### Post by squee on 2012-04-27
> **s.m.knipe said:**
> Bump

I am also having this wifi network password issue after upgrading to 12.04 LTS (was perfect on 11.10), and nothing I have found in searches thus far has helped...

I also HAD this issue. It disappeared after plugging the ethernet cable from the wifi router into my laptop. I couldnt connect to the wifi until after I did this. Strange...

---

### Post by Myoldmopar on 2012-04-27
I've encountered a problem like this on two machines, on two completely different networks.  It will just keep asking over and over.  If I right click on the network icon on the unity launcher and just say "quit", then all instances will close, and magically...the wireless will connect.  If I try to enter my password it will just keep on asking.  

Seems to happen real randomly (and annoyingly).  I tried upgrading a spare laptop to Precise and got a black screen on login, so I'll try Precise again after a few days and see if this network error ever occurs for me again.

---

### Post by tarkawebfoot on 2012-09-09
Just got a netbook and installed lubuntu on it. I had the issue where it kept asking me for my password on secured connections, and I found this thread. Note, this is not where it kept asking me for a pwd over and over. It just failed to store my pwd for my home network. Also, I know this thread was not about lubuntu originally.

Never the less, I thought the solution might be useful for some people. I went to Preferences --> Desktop Session Settings, and on the Automatically Started Applications tab, I selected GPG Password Agent, and all is well. Passwords are now stored normally.

Brian

---

