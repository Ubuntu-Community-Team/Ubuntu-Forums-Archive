---
title: "Here are directions to run Thinkorswim on Lubuntu 19.04"
date: 2019-05-13
forum: General Help
---

### Post by retrobeast on 2019-05-13
After installing Lubuntu 19.04 I could not get Thinkorswim to install.
Thanks to Michael in tech support from Thinkorswim there is a solution.
Here it is.

> [FONT=Arial] The following instructions should help you to install thinkorswim with the proper version of Java:[/FONT]

[FONT=Arial]Installing Zulu OpenJDK:[/FONT]

[FONT=Arial]1. Log in as root or use sudo[/FONT]

[FONT=Arial]2. Import Azul's public key                                 $ sudo apt-key adv --keyserver hkp://[/FONT][keyserver.ubuntu.com:80]("http://keyserver.ubuntu.com/")[FONT=Arial] --recv-keys 0xB1998361219BD9C9[/FONT]

[FONT=Arial]3. Add the Azul package to the APT repository[/FONT]

[FONT=Arial]For Ubuntu[/FONT]
[FONT=Arial]$ sudo apt-add-repository 'deb [/FONT][http://repos.azulsystems.com/ubuntu](http://repos.azulsystems.com/ubuntu)[FONT=Arial] stable main'[/FONT]

[FONT=Arial]For Debian[/FONT]
[FONT=Arial]$ sudo apt-add-repository 'deb [/FONT][http://repos.azulsystems.com/debian](http://repos.azulsystems.com/debian)[FONT=Arial] stable main'[/FONT]

[FONT=Arial]4. Update the information about available packages.[/FONT]

[FONT=Arial]$ sudo apt-get update[/FONT]

[FONT=Arial]5. Install Zulu by using the following command:                         $ sudo apt-get install zulu-8[/FONT]

[FONT=Arial]Once Zulu is installed move on to installing ThinkorSwim:[/FONT]

[FONT=Arial]1. Navigate to downloads and right click "thinkorswim_installer.sh", select "Properties"[/FONT]
[FONT=Arial]2. Select the "Permissions" tab, and make sure "Allow executing file as program" is selected[/FONT]
[FONT=Arial]3. Close the window[/FONT]
[FONT=Arial]4. Double click "thinkorswim_installer.sh"[/FONT]

[FONT=Arial]-IF ONLY A TEXT EDITOR OPENS, CLOSE IT AND CONTINUE BELOW-[/FONT]
[FONT=Arial]5. Click back onto the file explorer[/FONT]
[FONT=Arial]6. Open from the top menu bar:[/FONT]
[FONT=Arial]Edit > Preferences OR Files > Preferences[/FONT]
[FONT=Arial]7. Select the "Behavior" tab[/FONT]
[FONT=Arial]8. Select "Ask each time" OR "Ask what to do" under "Executable Text Files"[/FONT]
[FONT=Arial]9. Close the window and launch "thinkorswim.sh" and select "Run" from the prompt[/FONT]

[FONT=Arial]I hope this helps. If you need additional assistance feel free to contact our tech support team at XXX-XXX-XXXX[/FONT]

---

