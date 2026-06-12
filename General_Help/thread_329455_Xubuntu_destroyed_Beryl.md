---
title: "Xubuntu destroyed Beryl"
date: 2007-01-01
forum: General Help
---

### Post by raul_ on 2007-01-01
I installed xubuntu to check it out, didn't like it, removed it (i installed and removed it both with aptitude), logged in my normal session and i can't get Beryl to work now. When i removed xubuntu-desktop with aptitude i figured something was missing because the installation said that 300MB would be used and when i removed it said that only 74MB had been freed. so i want to the psychocats page and did the pure gnome instructions...here's the output:
```


(... a lot of not installed packages here....and then:)

Os seguintes pacotes foram instalados automáticamente e já não são necessários:
  beryl-core kdelibs4c2a emerald-themes linux-headers-generic ttf-thai-tlwg
  ttf-gentium vlc-plugin-alsa umbrello xscreensaver ubuntu-desktop libpcre3
  python-virtkey scim-modules-socket scim wxvlc libscim8c2a ttf-lao konsole
  scim-gtk2-immodule beryl-manager libberylsettings0 libt1-5 vlc-nox
  beryl-settings xpdf-reader vim-gnome libxine-main1 libxcomposite1
  ttf-arphic-uming libglib2.0-data im-switch beryl-plugins vim vlc
  ttf-arphic-ukai xli libxvmc1 xpdf vim-runtime onboard xine-ui totem-xine
  emerald linux-headers-2.6.17-10 libmodplug0c2 libemeraldengine0
  beryl-plugins-data totem gnome-accessibility-themes libjpeg-progs privoxy
  beryl totem-mozilla example-content linux-headers-2.6.17-10-generic libxine1
Utilize 'apt-get autoremove' para os remover.
Os seguintes pacotes serão REMOVIDOS:
  beryl beryl-core beryl-manager beryl-plugins beryl-settings emerald
  emerald-themes kdelibs4c2a konsole libberylsettings0 libemeraldengine0
  libglib2.0-data libjpeg-progs libmodplug0c2 libpcre3 libt1-5 libxcomposite1
  libxine-main1 libxine1 libxvmc1 privoxy totem totem-mozilla totem-xine
  ubuntu-desktop umbrello vim vim-gnome vim-runtime vlc vlc-nox
  vlc-plugin-alsa wxvlc xine-ui xpdf xpdf-reader xscreensaver
0 pacotes actualizados, 0 pacotes novos instalados, 37 a remover e 0 não actualizados.
É necessário fazer o download de 0B de arquivos.
Depois de descompactar, 111MB de espaço em disco serão libertados.
Você deseja continuar [Y/n]? n
Abortado.
raul@raul:~$ sudo apt-get autoremove
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências       
Reading state information... Pronto 
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
raul@raul:~$ 

```

the first list of packages were installed automatically and i should use apt-get autoremove to get rid of them...obviously apt-get autoremove didn't do nothing, as u can see...the second list of packages would be removed, but i see beryl in there and some packages i actually used...

How did xubuntu-desktop mess up my system like that?

EDIT: I should also point out that i can't select emerald by right clicking the beryl icon...it isn't there. I tried loading both programs manually and here's the output (note that the messages appear only when i try to reload the window manager)

```

raul@raul:~$ beryl-manager
raul@raul:~$ XGL Present
beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0
emerald --replace &
[1] 1727
raul@raul:~$ XGL Present
beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

```

---

### Post by raul_ on 2007-01-01
It seems that direct rendering stopped working...but i don't see how though...

```
raul@raul:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

is there anyway to enable it again? i saw some how to's here on the forums but i am damn sure that i didn't do that, and got it working :S

EDIT: seems that a reboot got it working again

---

