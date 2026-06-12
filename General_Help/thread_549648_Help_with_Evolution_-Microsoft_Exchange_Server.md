---
title: "Help with Evolution -Microsoft Exchange Server"
date: 2007-09-12
forum: General Help
---

### Post by Thug Nasty on 2007-09-12
Hello. Thanks for looking.

I'm running Kubuntu 7.04. I used Outlook prior to switching to Kubuntu and the exchange server worked flawlessly. I'd like to figure out how to make it work on Evolution. I have Evolution and evolution-exchanged installed. I've messed around with it all day with no luck. Here are the directions to connect to the exchange server through outlook: 
```

1. Under “Exchange Server Settings,” type “london.campus.up.edu” (without quotation marks) for the Microsoft Exchange Server.
2. Make sure the “Use Cached Exchange Mode” box is checked. 
3. Type your network username under the “User Name” field, then click the “More Settings” button. 
4. In the new “Microsoft Exchange Server” window that pops up, click on the “Connection” tab.
5.Under the “Exchange over the Internet” section at the bottom, check the “Connect to my Exchange mailbox using HTTP” box.
6. Click the “Exchange Proxy Settings” button.	
7. In the “Exchange Proxy Settings” window that pops up, type in “webmail.up.edu” under the “Use this URL to connect to my proxy server for Exchange” Check the box “On fast networks, connecting use http first, then connect using TCP/IP.”
8. Check the box “On slow networks, connecting use http first, then connect using TCP/IP.” In the drop down menu under “Proxy authentication settings,” select Basic Authentication.
9.  Click OK and then OK again to return to the “Exchange Server Settings” screen
Click Check Names.
In prompt box, enter “campus\username” for username, and network password.
Verify that the server and username get underlined.
10. Click Finish, then close out of the Mail section.
11. Open up Outlook 2003.
Log in with your network username, with the correct domain specified (Enter “campus” followed by a backslash and then your username, i.e. “campus\jdoe”), and your password. 

```

Any suggestions would be greatly appreciated. Here is what I have tried:
username: campus\'johnsmith'
username: 'johnsmith'
OWA URL: [http://london.campus.up.edu](http://london.campus.up.edu)
[https://london.campsu.up.edu](https://london.campsu.up.edu)
london.campus.up.edu
webmail.up.edu
[https://webmail.up.edu](https://webmail.up.edu)
[http://webmail.up.edu](http://webmail.up.edu)

I think I've pretty much tried every combination of the above with no avail. Any ideas? Thanks in advance.

John

---

### Post by dcstar on 2007-09-13
> **Thug Nasty said:**
> 
........
OWA URL: [http://london.campus.up.edu](http://london.campus.up.edu)
[https://london.campsu.up.edu](https://london.campsu.up.edu)
london.campus.up.edu
webmail.up.edu
[https://webmail.up.edu](https://webmail.up.edu)
[http://webmail.up.edu](http://webmail.up.edu)

I think I've pretty much tried every combination of the above with no avail. Any ideas? Thanks in advance.

John

None of those are OWA URLS, they are either Exchange URLs for direct Outlook client connections or another Web based interface, but not OWA.

The Evolution connector will only work with OWA.

---

### Post by Thug Nasty on 2007-09-13
hmm okay. I'll have to look into another option perhaps. Thank you for the reply.

---

### Post by perfecttao on 2007-10-12
Not sure if this topic is now resolved (and this is my first post as a Ubuntu newbie, but experienced Windows/Exchange Sysadmin) but if it is then hopefully it may help someone else down the line. I have managed to get Evolution working with Exchange 2003 (and in all honesty it was easier than getting Outlook to work using RPC over HTTPS - funny how MS native stuff doesn't work as well ;))

You will need to be able to connect to Outlook web Access using a web browser before you attempt with Evolution, for example going to [https://yourdomain.com/exchange](https://yourdomain.com/exchange).  By default Exchange server creates the OWA virtual directory in the root of the default website in IIS so chances are your path will be [http://london.campus.up.edu/exchange](http://london.campus.up.edu/exchange) or [https://http://london.campus.up.edu/exchange](https://http://london.campus.up.edu/exchange).  If you can't connect in a web browser you definitely won't be able to connect using Evolution.

when configuring Evolution, ensure that the path for the exchange server includes the Http:// or https://  as a preferred option (if the Exchange server forces SSL encryption) always use SSL otherwise be aware that any information (usernames/passwords etc) are sent in plain text!

after you've put in this information, stick in username and password test the connection by clicking "authenticate" 

Be aware that with a full mailbox it may take quite a while to scan and download content!

P

---

### Post by Vinnie_Fits on 2008-04-06
Well that sounds pretty nice. I got a little twist to add on to this though. I can access my exchange server on a windows machine via outlook using RPC over HTTPS. I can access my exchange server through OWA in Firefox on Ubuntu. Now here's the twist....

I'm a DOD employee who has to use a Common Access Card (CAC) (a smart card) to be able to use OWA (don't need it for RPC though). 

As you can probably figure out, I was able to download all the DOD root certificates needed and import then into FF, and I installed coolkey and pcsc. So all is fine and dandy in Firefox on Ubuntu. I even was able to find a source for actual certificates inside of the windows install for Root18a.exe and imported all those into Evolution.

Then I read your post above and found out Evolution will only support OWA. I followed the setup as you said but came to a dead end when authenticating during setup. I can't use a password for OWA, it's CAC only. Though I can use my password in Windows while using RPC Outlook.

I'm gonna figure this out somehow but would like some help.

Here's a previous post from me on how I enabled the use of the DOD CAC on my Ubuntu installation. [http://ubuntuforums.org/showthread.php?p=4666212#post4666212]("http://ubuntuforums.org/showthread.php?p=4666212#post4666212") 

The subject of my post is Quick and Dirty CAC install on Gutsy Gibbon. 

I appreciate any help in this matter. 

Thank you!

TAGS: OWA RPC PKI DOD Root18a.exe Evolution Exchange Outlook CAC Common Access Card Remote Outlook

---

### Post by unclecameron on 2008-06-05
I had OWA working fine for months, but now the security folks shut that down supposedly for security reasons...whatever.

Has anyone gotten RPC over https working on Evolution, that's the only tunnel I have left

---

### Post by arm-c on 2008-06-05
I am able to access Outlook Web Access using the DoD CAC Card.

My initial problem was I didn't know which certificate to use (actually, didn't notice I had an option).

If you are DoD, click the certificate to select the one ending in "email."

IS THERE A WAY TO DIGITALLY SIGN EMAILS in Evolution on Ubuntu?

---

