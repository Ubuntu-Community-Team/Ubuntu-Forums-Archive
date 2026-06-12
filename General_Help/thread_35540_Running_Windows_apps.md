---
title: "Running Windows apps"
date: 2005-05-19
forum: General Help
---

### Post by henriette_holm on 2005-05-19
Hi.
To make the final move from Windows XP to Ubuntu Linux - which I really, really want to do (getting fed up with dual booting) - I need to be able to run the following apps:

* Reference Manager ([http://www.refman.com/](http://www.refman.com/))
* ChemOffice ([http://www.cambridgesoft.com/](http://www.cambridgesoft.com/))

Can anyone point me in the right direction?
I've had a look at Crossover Office, Wine and VMWare - I haven't tried them though. Does anyone here have experince running any of the above two apps? Or even better, does anyone know of applications that will replace them?

- Henriette

---

### Post by psychicdragon on 2005-05-19
I've never tried either of these applications but it's really easy to see if they'll work under wine.

First add these extra repositories:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Then follow these steps to get your Windows partition mounted:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

then try this in the console:

sudo apt-get install wine

cd '/media/windows/Program Files/(dir)'

wine appname.exe

Hope this helps.

---

### Post by henriette_holm on 2005-05-20
ok, the install worked like a charm and I can run Notepad  :smile: 
I get an error though:

Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'

err:dc:CreateDCW no driver found for L"WINEPS"
fixme:winspool:AddPrinterW DocumentPropertiesW on printer 'L"DeskJet-950C"' fails
err:dc:CreateDCW no driver found for L"WINEPS"
err:dc:CreateDCW no driver found for L"WINEPS"
fixme:winspool:AddPrinterW DocumentPropertiesW on printer 'L"LaserJet-2200"' fails
err:dc:CreateDCW no driver found for L"WINEPS"


The printer bit is not important as I won't be printing anything but what about the language bit?

-Henriette

---

