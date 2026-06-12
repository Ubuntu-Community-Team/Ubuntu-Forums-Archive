---
title: "Help to install bubble upnp server"
date: 2017-06-06
forum: General Help
---

### Post by hilario_ferreira on 2017-06-06
Hi:

I'm trying to install bubble upnp serbver on my ubuntu 14.04.
I have been following these instructions 

[https://www.bubblesoftapps.com/bubbleupnpserver/](https://www.bubblesoftapps.com/bubbleupnpserver/)

when I enter the comand to install the server ( sudo apt-get install bubbleupnupserver) I get this result:

A ler as listas de pacotes... Pronto    = [COLOR=#ff0000]*reading package list ... ready*[/COLOR]
A construir árvore de dependências     =  [COLOR=#ff0000]*building dependence tree*[/COLOR] 
A ler a informação de estado... Pronto = [COLOR=#ff0000]*reading information state ... ready*[/COLOR]
Alguns pacotes não puderam ser instalados. Isso pode significar que = s*[COLOR=#ff0000]ome packages could not be installed , that means that you have asked for an impossible situation [/COLOR]*
você solicitou uma situação impossível ou se você está a usar a   -   [COLOR=#ff0000]*or that you are using an instable distribuition on which some demanded packages were not yet created  or were removed from the incoming*[/COLOR]
distribuição unstable em que alguns pacotes pedidos ainda não foram - [COLOR=#ff0000]*the following information can help to solve the situation:*[/COLOR]
criados ou foram movidos do Incoming.
A seguinte informação pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências não satisfeitas:  = [COLOR=#ff0000]*the next packages have no satisfied dependencies:*[/COLOR]
 bubbleupnpserver : Depende: init-system-helpers (>= 1.18~) mas 1.14ubuntu1 está para ser instalado  = [COLOR=#ff0000]*but ubuntu 1.14 is to be installed*[/COLOR] 
                    Depende: lsb-base (>= 4.1+Debian11ubuntu7) mas 4.1+Debian11ubuntu6.2 está para ser instalado  = [COLOR=#ff0000]*debian11ubuntu6.2 is to be installed*[/COLOR]
E: Não foi possível corrigir problemas, você tem pacotes mantidos (hold) estragados. [COLOR=#ff0000][I]it was not possible to solve problems , you have damaged packages
[/I][/COLOR]

What can I do to fix that ??

---

### Post by TheFu on 2017-06-06
Start with 
```
sudo apt update && sudo apt upgrade
```

Any errors?
Please use 'code tags' to post any* relevant issues* so things line up and are easier to read.

---

### Post by hilario_ferreira on 2017-06-06
> **TheFu said:**
> Start with 
```
sudo apt update && sudo apt upgrade
```

Any errors?
Please use 'code tags' to post any* relevant issues* so things line up and are easier to read.

Hi TheFu

I don't see any errors after entering that command

---

### Post by SeijiSensei on 2017-06-06
If you want a DLNA server, you might be better off choosing minidlna, which I use, or Kodi.

---

### Post by hilario_ferreira on 2017-06-06
> **SeijiSensei said:**
> If you want a DLNA server, you might be better off choosing minidlna, which I use, or Kodi.

I tried to install minidlna before but had same kind of errors.
Concerning kodi It don't give me remote access that's why I prefer bubble or minidlna

---

### Post by SeijiSensei on 2017-06-06
Did you try using this?

[https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA)

---

### Post by hilario_ferreira on 2017-06-07
No but I'm trying to do it now.

Firs step ok.

2nd : I think I have to go to etc/mini dlna.conf and change accordingly to the instructions but do I have to delete everything inside and replace for the globally configuration ?? I tried that but when I save it tells me I have no permission !

---

### Post by SeijiSensei on 2017-06-07
You have to edit that file as the "root" (admin) user via sudo:

```
sudo nano /etc/minidlna.conf
```

All you need to do is add one or more media_dir lines specifying the locations of the files to be served.  On my machine, I have
```
media_dir=A,/media/raid/Music
media_dir=V,/media/raid/anime
```
Both these directories are on my RAID array.  The "A" and "V" codes designate them as an audio and a video directory respectively.  I made no other changes to the file.  

You'll then have to restart the server with "sudo systemctl restart minidlna" since you're on 16.04.

---

### Post by hilario_ferreira on 2017-06-07
> **SeijiSensei said:**
> You have to edit that file as the "root" (admin) user via sudo:

```
sudo nano /etc/minidlna.conf
```

All you need to do is add one or more media_dir lines specifying the locations of the files to be served.  On my machine, I have
```
media_dir=A,/media/raid/Music
media_dir=V,/media/raid/anime
```
Both these directories are on my RAID array.  The "A" and "V" codes designate them as an audio and a video directory respectively.  I made no other changes to the file.  

You'll then have to restart the server with "sudo systemctl restart minidlna" since you're on 16.04.

Sorry SeijiSensei but I'm on 14.04.

Ok I understand now , but I have one folder for movies and another one for tv shows how do I have to add them ?? what do you mean by RAID ??

---

### Post by SeijiSensei on 2017-06-07
Use "sudo service minidlna restart" to restart the server then.

---

### Post by hilario_ferreira on 2017-06-07
Ok I have following doubts:

I have to delete everything inside etc/minidlna.conf  ?? and add media_dir=A, for audio files ?? and media_dir=V, for video files ???
My music patth is : /home/hilario/musica    I must add " media_dir=A,/home/hilario/musica ??? is this correct ???

---

### Post by hilario_ferreira on 2017-06-07
I'm sorry but I didn't manage to do it.

When I enter : 
"sudo nano /etc/minidlna.conf"   I add media_dir=A,/home/hilario/musica  then I add media_dir=A,/home/hilario/FILMES 
Then When I leave the terminal there's a message "there's a process being executed in this terminal coling it will kill that task !!! what shall I do ???

---

### Post by SeijiSensei on 2017-06-07
Did you save the file and close nano first?

Make your additions, then hold down the Ctrl key and hit "x". Type "y" when asked to save the file. Now you can restart minidlna.

Nano has a useful menu of commands at the bottom of the screen. The "^" symbol means "hold down the Ctrl key."

---

### Post by hilario_ferreira on 2017-06-07
Ok I found how to do it.

But now I have the folowing doubts.

I couldn't manage to make it play the subtitles (subs are in separated srt files with same name of the movies).
Also I think I can't reach the dlna remotely (from outside of my wifi) .Right ??

---

### Post by SeijiSensei on 2017-06-07
I believe DLNA is always limited to the local network, but I'm no expert on the subject.

I also don't know if DLNA will handle external subtitle files, though I doubt it.  Most everything I watch is in the Matroska (".mkv") container where the subtitles are included in the file.  I can watch shows like that on my Android phone with Bubble UPnP and MXPlayer.  The former just handles the transmission, the latter plays the files and decodes the subtitles.

It's possible to [re-encode videos with external subtitle files into the mkv container using ffmpeg]("https://stackoverflow.com/questions/8672809/use-ffmpeg-to-add-text-subtitles").  It's also possible to encode them in the mp4 container, though it's not as flexible as Matroska.  However more media devices like TVs support mp4 than mkv, so the correct answer for you depends on the devices you intend to use to play the videos.

---

### Post by hilario_ferreira on 2017-06-07
Thanks for your explanations.

I think I wil stay with plex although I'm having problems with subtitles too but only on tv shows !!! it's strange but it's true.
All movie play correctly with subs, but tv shows I have problems because plex server is not detecting those subs !!!

Ok thank you once again.
I think we can close this thread.

---

### Post by SeijiSensei on 2017-06-08
One other alternative to consider might be [ps3mediaserver]("https://help.ubuntu.com/community/Ps3MediaServer").  It can do on-the-fly transcoding from unsupported formats to supported ones.

If you're done with this thread, go to the "Thread Tools" at the top and mark it "[SOLVED]".

---

