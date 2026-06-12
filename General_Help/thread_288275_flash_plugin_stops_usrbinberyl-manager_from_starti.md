---
title: "flash plugin stops /usr/bin/beryl-manager from starting correctly"
date: 2006-10-29
forum: General Help
---

### Post by wootton on 2006-10-29
Hello all,

I have recently installed Ubuntu Dapper Drake with XGL, Compiz and Beryl. I followed [FONT="Courier New"]http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Post-install_configuration[/FONT] to install. 

Beryl is started by adding 

[FONT="Courier New"]/usr/bin/beryl-manager[/FONT]

to the startup session (as recommended by [FONT="Courier New"]http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Post-install_configuration[/FONT]).

Since installing the flash plugin from adobe's site beryl and therfore xgl, compiz don't load correctly and the fallback window manager is selected, or, no window manager is selected and no minmise, close, shade, unshade etc etc. buttons exist around any applications.

If I start the manager manually by running

[FONT="Courier New"]/usr/bin/beryl-manager[/FONT]

and then do Ctrl+Alt+Del then it is OK.  But as soon as I restart the system, Beryl will not load correctly.

---

### Post by jocko on 2006-10-29
> **wootton said:**
> Hello all,

I have recently installed Ubuntu Dapper Drake with XGL, Compiz and Beryl. I followed [FONT=Courier New]http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Post-install_configuration[/FONT] to install. 

Beryl is started by adding 

[FONT=Courier New]/usr/bin/beryl-manager[/FONT]

to the startup session (as recommended by [FONT=Courier New]http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Post-install_configuration[/FONT]).

Since installing the flash plugin from adobe's site beryl and therfore xgl, compiz don't load correctly and the fallback window manager is selected, or, no window manager is selected and no minmise, close, shade, unshade etc etc. buttons exist around any applications.

If I start the manager manually by running

[FONT=Courier New]/usr/bin/beryl-manager[/FONT]

and then do Ctrl+Alt+Del then it is OK.  But as soon as I restart the system, Beryl will not load correctly.

I don't think it has anything to do with flash. Try adding '/usr/bin/beryl-xgl' to the session startup programs, that solved the same problem for me a couple of weeks ago.

---

### Post by wootton on 2006-10-29
Brilliant, worked.  Although on first reboot I lost the title bar and almost everything.  Got the terminal window up, and rebooted again, and it all seems fine.

Thank you.

---

