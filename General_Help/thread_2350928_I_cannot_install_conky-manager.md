---
title: "I cannot install conky-manager?"
date: 2017-01-29
forum: General Help
---

### Post by ayoquo on 2017-01-29
Hi there,

I cannot install conky manager. I am issuing the commands as follows:

```
sudo apt-add-repository -y ppa:teejee2008/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install conky-manager
```

After all that, it's saying ```
unable to locate package conky-manager
```

What's going on here, is anyone able to assist me? 

Thanks.

---

### Post by Perfect Storm on 2017-01-29
Which version of lubuntu are you using. I've been looking through the ppa and the support only up to 16.04 - [https://launchpad.net/~teejee2008/+archive/ubuntu/ppa](https://launchpad.net/~teejee2008/+archive/ubuntu/ppa)

---

### Post by RobGoss on 2017-01-29
I've installed the same using the codes you've posted works for me after running those commands. I'm using Ubuntu 16.04

---

### Post by sevenday4 on 2017-10-16
> **ayoquo said:**
> Hi there,

I cannot install conky manager. I am issuing the commands as follows:

```
sudo apt-add-repository -y ppa:teejee2008/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install conky-manager
```

After all that, it's saying ```
unable to locate package conky-manager
```

What's going on here, is anyone able to assist me? 

Thanks.

I have found an interesting way to get conky manager to work. And, I got it to work on Ubuntu 17.10 no less (Artful)! What I did was installed the GNOME shell, then installed these Add-ons 
**gnome-3-24 **and **gnome-3-26-1**

These include the snap for GNOMES 3.24 & 3.26 stack (the base libraries and desktop  integration components) and shares it through the content interface.  It's built using the Ubuntu xenial backport binaries.

I then went to this website:
                        [https://www.linuxbabe.com/ubuntu/install-conky-manager-ubuntu-16-04-17-04](https://www.linuxbabe.com/ubuntu/install-conky-manager-ubuntu-16-04-17-04)
  
Where I went to where you see this section that follows:

      The above PPA doesn&#8217;t support [Ubuntu 17.04 ]("https://www.linuxbabe.com/ubuntu/upgrade-ubuntu-16-10-to-17-04")yet. If you use the above PPA on Ubuntu 17.04, you would see the following error. Unable to locate package conky-manager Ubuntu 17.04 users can download Conky Manager Deb file.
 
64 bit
 wget [https://launchpad.net/~teejee2008/+archive/ubuntu/ppa/+files/conky-manager_2.4~136~ubuntu16.04.1_amd64.deb](https://launchpad.net/~teejee2008/+archive/ubuntu/ppa/+files/conky-manager_2.4~136~ubuntu16.04.1_amd64.deb) 

32 bit
 wget [https://launchpad.net/~teejee2008/+archive/ubuntu/ppa/+files/conky-manager_2.4~136~ubuntu16.04.1_i386.deb](https://launchpad.net/~teejee2008/+archive/ubuntu/ppa/+files/conky-manager_2.4~136~ubuntu16.04.1_i386.deb) 

Then install it with **gdebi**, which will automatically handle package dependencies.
 
sudo apt install gdebi

sudo gdebi conky-manager*.deb  

Now depending on what architecture of your machine will determine which package to use. But the major take away is that you have to have your desktop to be in GNOME for this to work. Now, will conky manager work if you remove gnome, **NO!** Remember the xenial backport binaries that had to be installed. But, I could be wrong on this conjecture. Happy conky and God bless!):P

---

### Post by cablat on 2017-12-10
EU FIZ OS SEGUINTES PASSOS E FUNCIONOU NO UBUNTU STUDIO 17.10

EM MODO TEXTO

BAIXEI O PACOTE NO REPOSITORIO DO 16.04  CONKY-MANAGER

$ sudo dpkg -i conky_1.10.6-1.1_all.deb 
A seleccionar pacote anteriormente não seleccionado conky.
(Lendo banco de dados ... 296967 ficheiros e directórios actualmente instalados.)
A preparar para desempacotar conky_1.10.6-1.1_all.deb ...
A descompactar conky (1.10.6-1.1) ...
Configurando conky (1.10.6-1.1) ...

$ sudo dpkg --configure -a
dpkg: problemas com dependências impedem a configuração de conky-manager:
 conky-manager depende de realpath; porém:
  Pacote realpath não está instalado.
dpkg: erro ao processar o pacote conky-manager (--configure):
 problemas de dependência - deixando desconfigurado
Erros foram encontrados durante o processamento de:
 conky-manager


$ sudo apt install realpath
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Os NOVOS pacotes a seguir serão instalados:
  realpath
0 pacotes atualizados, 1 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
1 pacotes não totalmente instalados ou removidos.
É preciso baixar 1.086 B de arquivos.
Depois desta operação, 25,6 kB adicionais de espaço em disco serão usados.
Obter:1 [http://ubuntu-archive.locaweb.com.br/ubuntu](http://ubuntu-archive.locaweb.com.br/ubuntu) artful/main amd64 realpath all 8.26-3ubuntu4 [1.086 B]
Baixados 1.086 B em 1s (1.082 B/s)
A seleccionar pacote anteriormente não seleccionado realpath.
(Lendo banco de dados ... 296971 ficheiros e directórios actualmente instalados.)
A preparar para desempacotar .../realpath_8.26-3ubuntu4_all.deb ...
A descompactar realpath (8.26-3ubuntu4) ...
Configurando realpath (8.26-3ubuntu4) ...
Configurando conky-manager (2.4~136~ubuntu16.04.1) ...


$ sudo dpkg --configure -a


$ sudo apt-get install -fLendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.

---

### Post by QIII on 2017-12-10
@cablat:

This is an English speaking Forum.  Please translate your post into English if you intend for this to be an answer to the original post.

If you would like a member of the Forums Staff to move your post to the [Portugal LoCo Forum]("https://ubuntuforums.org/forumdisplay.php?f=462"), please click the request button and request the move.  To my knowledge there is only one Portuguese-speaking member of the Forums Staff, but I am sure he would be quite happy to help you get this to the right place.

---

