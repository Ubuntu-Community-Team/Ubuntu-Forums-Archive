---
title: "Pantum P2500W/P2502W WiFi Printer Setup Instructions"
date: 2015-11-16
forum: General Help
---

### Post by Jack_Roman on 2015-11-16
Good day, I recently purchased a Pantum P2502W laser printer. The "w" at the end of the model number stands for WiFi. Anyway it took me a few days of searching all over various Linux (Ubuntu) and non-Linux related forums to figure out how to add this printer and set up wiFi on two laptops one running version 14.04.3 and 15.10 Ubuntu distributions. This is because the instructions for setting up Wifi are really targeted at Windows. Just so you know, the instructions I am about to provide will work for setting up Wifi on any Pantum laser printer with Wifi capability. If you follow the same steps as I have, you will have this inexpensive but very fast and efficient laser printer setup on in no time!

The following step-by-step instructions listed below assumes you are using a router to manage your wireless network. 
Total time: 10 minutes.


1. First go to Pantum Website and download the Linux Driver here:
[http://global.pantum.com/global/index.php?option=com_virtuemart&view=supportdetails&pid=33&Itemid=108](http://global.pantum.com/global/index.php?option=com_virtuemart&view=supportdetails&pid=33&Itemid=108)  or alternatively you can navigate to [www.pantum.com](www.pantum.com) and once on the home page click on Support
Under browse by product select P2500 Series. 


2. (You can skip Steps 2 and 3 if you have already downloaded the P2200-P2500 Linux drivers) Then you will see various models of P2500 Series printers. Click on the model P2500W as this indicates you have the Wireless model. This will take you to the Download Drivers, Manuals page for the P2500W model. <see link below>
[http://global.pantum.com/global/index.php?option=com_virtuemart&view=supportdetails&pid=33&Itemid=108](http://global.pantum.com/global/index.php?option=com_virtuemart&view=supportdetails&pid=33&Itemid=108)


3. Scroll down and under description look for the driver Pantum P2200-P2500 Series Linux Driver. Under OS you will see Ubuntu 12.04LTS This will work for all Ubuntu OS versions 12.04LTS and higher. Click on the Download button to the right and wait until the download is completed.


4. Once the printer driver download is complete go to your Download folder. You will need to extract the file. After extracting the file, you will see a folder labeled, "20150901 Pantum P2200-P2500 Series Linux Driver V1.80" folder. Click on this folder.  Inside that folder you should see another folder called "Linuxinstall". Click it on and then another folder called "Resources". Click on the "Resources" folder and choose the Debian file folder that matches your computer (32 bit or 64 bit). This will then launch the Ubuntu Software Center App to install the driver. If for some reason it does not automatically begin installing the printer driver, just type in P2500 and it will display the driver to install and click on install.


5. Once the Pantum printer driver has been installed close out the Ubuntu Software Center. Then go to Printers and click on the Plus symbol to add a Printer.


6. Once you select the add printer you will be on the "Select Device" dialog window. Under Devices, from the list on the left, click on the LPD/LPR Host or Printer. To the right, under Location of the LPD Network printer, is a label called, Host with a blank field to the right. Type in LPD/LPR. Leave the Queue field blank and then click the Forward button below that.


7. By default the "Select printer from database" radio button will already be selected and a list of printer manufacturers by name will be displayed below. Scroll through the list until you locate Pantum. Click on Pantum and then click the Forward button.


8. The Pantum models should be displayed. Choose the P2500W as your printer. Your Printer should now be installed in the Printers list.


9. You will now setup the printer's Wifi to your Router. At this point you should power up the printer and once powered up, click and release the 'Cancel/Continue' button and then the Wifi button on your Pantum P2502W printer.
Next you will press your router's WPS connection button.  




10. At this point you should be able see the Pantum printer on your list of Access Point connections. It will look something like this: Pantum-AP-083C53.


11. Next access the Pantum printer Access Point (AP) by clicking on it and then connecting to it. It should connect automatically without any password login.  Next Launch your web browser and type in the IP addres for the Pantum printer. This should be 192.168.223.1  


12. This will load the Pantum Admin page. Click on login. For username enter admin. Under password enter six zeroes (000000). Then click the login button on the lower left.


13. After you have logged in go to the Admin Settings to change your password. It is important to write down and save your password and secure it in a safe place. I recommend entering it in a log book. Once you have entered a new password click the Changes button. You will receive a successful submission notification once the password has been changed. Keep in mind that you can only change the password not the User ID. This is set always as Admin. Note: any time you make changes anywhere in the Pantum Admin  web page you will receive a successful submission notification. 


14. Next, Click on the Settings. Go to the IPv4 located under the Network Settings/Protocol Settings. If your Router is set to automatically assign IP addresses, leave this setting alone. If you have a static setting in your router then change Automatic to Manual to the right of IPv4 Address Assignment Mode. Note: The IPv4 Address should already be loaded in the appropriate fields from your router. If not you will have to input them manually. Then, click the Apply button.


15. Remain on Settings and Go to "Wireless Settings" and click on "Wireless Network". To the Right you should see Basic Status of Wireless Network. Click the "Turn on" radio button to enable the printer's Wifi access. 


16. Below that you should see Search for hotspot Refresh. You really do not need to click Refresh as your router's Wireless network should already be listed. Just go to the Authentication section and type in your Wireless network's name. Under Authentication choose WPA/WPA2. Then scroll down to input your Wireless network's password and click apply.


17. Lastly, click on the Wireless Hotspot. There, you should see the settings for the Pantum AP or accesspoint. It is here where you can secure the access to your Pantum Wifi security settings. Go to the section titled Wireless Parameter and in the field titled "Authentication" choose WPA2 then right below the Password field enter a password for the Panthum AP. I suggest using the same password as your wireless network. Enable DHCP Service should be selected as "Turn on". Then click the Apply button when done. At this point, you should notice that your Wireless network connection has been automatically re-established. Now log out of the Pantum Admin web page and close out your web browser.


18. Go back into Printers and click on the Pantum P2500W printer. To the right of Settings, locate the Device URI field and click the Change... button. Once there, it should take a few seconds for the Select Device information list on the left to load. The Pantum P2500W printer should already be found. (If not Click the find Network Printer to locate it). Then click the Apply button to complete the wireless connection via DNS-SD. You will notice that a new Icon called ipp is also in your Printers listing. DO NOT DELETE THIS!!! this is the wireless settings that controls access to your Pantum printer. **By the way, if you have other Ubuntu PCs to setup to access your Pantum P2502W printer, all you have to do is download the Pantum printer driver on those PCs and once installed on the Ubuntu pc it will just automatically connect to your router.

This completes the entire installation and wireless setup. Remember you only have to do this once and only for the primary pc/laptop when you make your first connection. I have one other Wifi enabled printer setup on my network (different manufacturer) and can print from either that or the Pantum P2502W with no issues. This should work just as well for anyone following these instructions.


NOTE: For any future changes in the Pantum Printer wireless connection you must remember to access the Admin page by logging into the Access point for your Pantum P2500W Wireless printer.

---

### Post by joi on 2016-01-30
Thank you. I am planning to buy that laser printer. By any chance, does it have a scanner? I really need a scanner function if not I'll move on to something else

---

### Post by howefield on 2016-01-30
> **joi said:**
> Thank you. I am planning to buy that laser printer. By any chance, does it have a scanner? I really need a scanner function if not I'll move on to something else

If that is a serious question, no it doesn't.

Try the manufacturers website for specification details.

---

### Post by arvana2 on 2016-06-15
Thanks very much, @[**[COLOR=#000000]Jack_Roman[/COLOR]**]("http://ubuntuforums.org/member.php?u=1990475") -- very helpful guide!

---

### Post by ddalley on 2017-04-19
The link to the driver needs updating to: [http://global.pantum.com/global/drive/2500w/](http://global.pantum.com/global/drive/2500w/)

Then select the Linux button.

So far, I have not been able to get your steps to work with Linux Mint Mate. I don't think the printer is connecting to the SmartRG router through WPS.

---

### Post by jeff-james-a on 2018-02-17
Pantum web sites are down, showing error 502 - Bad Gateway.

---

### Post by phifgo on 2018-05-22
I follow these instructions but...... it doesn'tr  work in Ubuntu 18.04.
Then I found  this [https://medium.com/the-sysadmin/google-cloud-print-on-ubuntu-16-04-in-10-minutes-1f0bf97ba9d3](https://medium.com/the-sysadmin/google-cloud-print-on-ubuntu-16-04-in-10-minutes-1f0bf97ba9d3)  article , I trierd  cups with Google cloud Print and  now it works perfectly.

---

