---
title: "Google Earth won't load"
date: 2013-05-08
forum: General Help
---

### Post by adambond on 2013-05-08
When I click on google earth, the 'Google Earth' title screen pops up for about 2 seconds, then goes away. 
And no google earth. :confused:
So I reinstalled it. No dice. Same result. 
So I downloaded it again. No dice. Same result. 

Im sure its an easy fix. Just dont know it.

---

### Post by tdockery97 on 2013-05-08
Just to make sure that you're not missing dependencies, open Terminal and type:

```
sudo apt-get -f install
```

---

### Post by Impavidus on 2013-05-08
Try starting it from a terminal:```
google-earth
```It may give you an error message. If it says```

Google Earth appears to be running already. Please kill the
 existing process, or delete /home/your_user_name/.googleearth/instance-running-lock if this is an error.

```
then do what it says. Google earth uses a lock to make sure only one instance of it runs at the same time. If the lock wasn't properly removed it fails.

---

### Post by 3rdalbum on 2013-05-08
Two possibilities I can think of:

1. You downloaded Google Earth without using a .deb package or the repository, and you are missing a dependency (something Google Earth needs in order to run). If you run Google Earth from the terminal as described above, you will be able to see what is missing.

2. You don't have 3D acceleration on your graphics driver. If you have Nvidia or recent ATI graphics you need to install the driver.

---

### Post by nairias on 2013-05-09
I have the same problem.

AMD APU A3400 (Llano) w/o any external graphics, 8GB RAM, fresh install of 13.04, no problems with the previous 12.10;

With video drivers: AMD from FGLRX-updates (proprietary) and AMD from FGLRX (prorpietary) Google Earth will just not load.

With xorg it loads but doesnt display the terrain - i.e. it displays the Earth is if it was completely transparent, with names of the cities, borders of the countries, other landmarks etc. on it.

Starting from terminal makes no difference in both the above-mentioned cases, giving off this message when AMD drivers are on: 
"
[0509/081628:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0509/081629:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0509/081629:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0509/081629:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
Google Earth has caught signal 11.
"

and this one with xorg:
"
[0509/082410:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
[0509/082410:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
[0509/082410:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0509/082410:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0509/082411:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[0509/082411:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
[0509/082411:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
"

"sudo apt-get -f install" gives off "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

----------------
edit: all the above with the latest GE version 7.1.1.1580

---------------- 
edit2 - [SEMI-SOLVED]:
 - installed libfreeimage3 (sudo apt-get install libfreeimage3)  (don't know if it helps, did it in hope to make the GE7 work, it didn't)
 - uninstall GE 7
 - build the GE package myself with (sudo apt-get install googleearth-package) (sudo make-googleearth-package --force) which gave me a nice googleearth_5.2.1.1588+0.7.0-1_amd64.deb
 - tried to install (sudo dpkg -i googleearth_5.2.1.1588+0.7.0-1_amd64.deb), some dependencies are not met, so
 - sudo apt-get -f install (beware, it installs some MS fonts in my case, beware2: if you decide to install them, make sure to click "yes")
 - once again sudo dpkg -i googleearth_5.2.1.1588+0.7.0-1_amd64.deb 
 - it works perfectly with the proprietary AMD drivers installed via the Software and Updates from the Dash, with the xorg drivers it works fine but slightly slower
 - semi-solved since it's the old GE version, which - though being fully functional for my purposes - is still the old version and not the latest one, and the MS fonts were installed :)

---

### Post by Rekhillbill on 2013-06-14
I have 13.04 (Raring Ringtail) and an AMD64-bit system.  Google Earth worked in 64-bit version for awhile, then only the splash screen would appear and the program would not boot.

I tried the 32-bit version, as suggested in the following link, and Google Earth is working OK again.

I do receive the same error msg in the terminal, i.e., "No URLRequestContext for OCSP Handler." but Google Earth boots up OK from the terminal or from the icon.

[http://askubuntu.com/questions/296718/google-earth-7-1-crashing-after-showing-splash-screen?answertab=votes#tab-top](http://askubuntu.com/questions/296718/google-earth-7-1-crashing-after-showing-splash-screen?answertab=votes#tab-top)

---

