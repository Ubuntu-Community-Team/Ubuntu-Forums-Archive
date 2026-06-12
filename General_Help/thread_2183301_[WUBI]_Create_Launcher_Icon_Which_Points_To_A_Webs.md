---
title: "[WUBI] Create Launcher Icon Which Points To A Website"
date: 2013-10-24
forum: General Help
---

### Post by superduper2 on 2013-10-24
Hi All

I know there have been several questions asked in regard to creating custom Launcher Icons but all of them I have come across seem to relate to creating a launcher for a custom program or the like.

My enquiry is a little different though.....

I would like to know if it is possible (and usually it is somehow) to create a custom Launcher icon along with a custom image which will open to the Outlook.com online email app via the Firefox browser.

I was able to do this easily enough in Windows by entering the following into the Target field of a New Shorcut: 
"C:\Program Files (x86)\Mozilla Firefox\firefox.exe" and then adding the outlook URL to the end of that.

I have read around about the different methods of creating a Launcher icon but am somewhat stumped other than the fact that firefox resides in usr/bin/firefox.

Would anybody please be able to point me in the right direction here? 

What would be the full path I would need to enter in Main Menu -> Create new launcher (if in fact that is what I need to do to accomplish this task) to point me to the outlook.com sign in page as I did in Windows via a Desktop shortcut? After that, once again if Create New Launcher is what actually needs to be done, how do I add the image of my choosing as there seems to be no option to navigate to an image? 

I know that Thunderbird is available and would be a breeze to attach to the Launcher but I am not interested in using an email client.

If anyone could post some detailed instructions that would be great - thanks in advance for any help you may be able to provide.

---

### Post by superduper2 on 2013-10-27
OK - first of all sorry for double posting.

I am not trying to bump my thread up the list but simply put, I still need help after trying a lot of things in regard to my issue.

I have managed to get a working Launcher icon happening but I cannot open the target URL without getting an error from Microsoft - I will explain:

I have created an outlook.desktop file which I have saved to the /home/Documents directory. I have done this so that a "shortcut" does not actually appear on the Desktop (please tell me where I should actually store this as I tried to save the file to [HIGHLIGHT][COLOR=#ff0000]/usr/share/applications/outlook.desktop[/COLOR][/HIGHLIGHT] but gedit will not allow saving the file to that location).

Here is the code for the .desktop file I created:
```

[Desktop Entry]
Version=1
Name=OultookEmail
Comment=Launches Outlook.com Sign In Page In Firefox Browser 
Exec=firefox https://login.live.com
Icon=/home/myusername/Pictures/UnityLauncherIcons/outlook.png
Terminal=false
Type=Application
Categories=Utility;Application;

```

After doing this I right clicked the newly created outlook.desktop file and set the properties to allow execution.

The custom image I created at 48 x 48 pixels was picked up. I double clicked the icon from the Documents location and it launched to the target URL without issue.

I then tried to drag the icon to the Unity Launcher but was unable to do so......... so I removed the execute property from outlook.desktop, then dragged the icon to Unity Launcher which then allowed attachment. After this I set the properties back to executable for outlook.desktop which then re-added the custom image to both the Documents location and Unity Launcher. I tested each and was able to launch from both locations.

The problem I am facing though is that after signing in to [https://login.live.com](https://login.live.com) it does not load directly to the Outlook.com email Inbox - which is understandable because this URL is basically the place to access all the settings for a Microsoft account.

I tried using the URL associated directly with the outlook.com Sign In page as it will take the user directly to their outlook.com Inbox.

The EXEC= shows the path in the code below:

Therefore I resaved the file as follows:
```

[Desktop Entry]
Version=1
Name=OultookEmail
Comment=Launches Outlook.com Sign In Page In Firefox Browser 
Exec=firefox https://login.live.com/login.srf?wa=wsignin1.0&ct=1382843105&rver=6.1.6206.0&sa=1&ntprob=-1&wp=MBI_SSL_SHARED&wreply=https:%2F%2Fmail.live.com%2F%3Fowa%3D1%26owasuffix%3Dowa%252f&id=64855&snsc=1&cbcxt=mail
Icon=/home/daltrain/Pictures/UnityLauncherIcons/outlook.png
Terminal=false
Type=Application
Categories=Utility;Application;

```
When the page loads it returns the error:
> 

[B]We're unable to complete your request
[/B]
Microsoft account is experiencing technical problems. Please try again later.


I tested if the Microsoft server is in fact encountering any difficulties and or if there is indeed an issue with my account by: Google Search-> Type Outlook and hit enter -> Click the Sign In link which returns the sign in page at the same URL which if added to outlook.desktop throws the error -> Sign in with username and password -> Access straight to my Outlook.com email Inbox............ therefore ZERO issue via Firefox ->Google, the Microsoft server OR my account. 

The good news here is that I learned how to create a .desktop launcher, was  able to add it to Unity and it worked............it won't point to the  Target I want it to without error ...... but it worked!! 

Can someone PLEASE explain to me what is going on here - is it possible that this is Firefox related? Is there a setting I can possibly change that will work for me? 

I am out of ideas here guys and after a lot of time spent trying to find a solution I am in need of your help.

EDIT: Have run this command via Terminal and can supply the output if need be.

---

