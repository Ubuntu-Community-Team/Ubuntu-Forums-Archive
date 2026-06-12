---
title: "WinAVI with wine, help please"
date: 2006-08-29
forum: General Help
---

### Post by simoncoul on 2006-08-29
Hi I'm trying to run WinAvi with wine as it is one of the best video converts I'm used back in the windows days.   I keep getting this erros

```

$ wine "C:\program files\WinAVIVideoConverter\winavi.exe"
fixme:atl:AtlModuleInit SEMI-STUB (0x3f5348 0x3f5000 0x3f0000)
err:ole:CoGetClassObject class {7c23220e-55bb-11d3-8b16-00c04fb6bd3d} not registered
err:ole:CoGetClassObject no class object {7c23220e-55bb-11d3-8b16-00c04fb6bd3d} could be created for context 0x1
err:ole:CoGetClassObject class {765035b3-5944-4a94-806b-20ee3415f26f} not registered
err:ole:CoGetClassObject no class object {765035b3-5944-4a94-806b-20ee3415f26f} could be created for context 0x1
err:seh:setup_exception nested exception on signal stack in thread 0015 eip 7efd56b8 esp 7ffddc00 stack 0x231000-0x340000


```



If you do not know how to do this it would also be helpful if you knew of a program for linux that transcodes but allows you to set the output file size and burn KVCD?

Thanks for the help

---

### Post by orb9220 on 2006-09-07
try sudo wine

---

### Post by PapaWiskas on 2006-09-08
I use TOVID, a linux app to do all my transcoding of DVD and VCD/SVCD etc...

I DONT however use the TOVID GUI interface, it is way too buggy for me....I use the command line for TOVID, its not scary and really easy to use once you start using it.

---

### Post by simoncoul on 2006-10-21
Sorry took so long to respond, thank you for the respones but I was not able to get it too work.

Does anyone know of a video converting program that allows you to set the size of the output file?

---

### Post by bhuthogg on 2007-06-25
i know this an old post but i came across it by google looking for something similar..

its took me ages to find this and it was just pure fluke 

anyways the closest thing i have found is [COLOR="Red"]devede 3.0-1[/COLOR]  here [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

perfect for divx to dvd or vcd

i already have automatix installed and think thats got the codecs sorted

old post plz dont flame me :)

---

### Post by ElemonGW on 2007-07-23
WinAVI 's gui cannot run at all under wine. This is the wine's output when you try to run it:
```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:ole:CoGetClassObject class {7c23220e-55bb-11d3-8b16-00c04fb6bd3d} not registered
err:ole:CoGetClassObject no class object {7c23220e-55bb-11d3-8b16-00c04fb6bd3d} could be created for context 0x1
err:ole:CoGetClassObject class {765035b3-5944-4a94-806b-20ee3415f26f} not registered
err:ole:CoGetClassObject no class object {765035b3-5944-4a94-806b-20ee3415f26f} could be created for context 0x1
err:ole:CoGetClassObject class {238d0f23-5dc9-45a6-9be2-666160c324dd} not registered
err:ole:CoGetClassObject no class object {238d0f23-5dc9-45a6-9be2-666160c324dd} could be created for context 0x1
Segmentation fault (core dumped)

```
However there is a command line version of WinAVI, located in the installation folder called WinAVIMp4cmd. This causes also erros and cannot run, but there are probably more chances making it work instead of the gui version. This is what wine reports when trying to run it:
```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:ole:CoGetClassObject class {64697678-0000-0010-8000-00aa00389b71} not registered
err:ole:CoGetClassObject no class object {64697678-0000-0010-8000-00aa00389b71} could be created for context 0x1
err:ole:CoGetClassObject class {78766964-0000-0010-8000-00aa00389b71} not registered
err:ole:CoGetClassObject no class object {78766964-0000-0010-8000-00aa00389b71} could be created for context 0x1
err:ole:CoGetClassObject class {46540009-5a4a-534f-4654-5a4a534f4654} not registered
err:ole:CoGetClassObject no class object {46540009-5a4a-534f-4654-5a4a534f4654} could be created for context 0x1
err:ole:CoGetClassObject class {f50b3f13-19c4-11cf-aa9a-02608c9baba2} not registered
err:ole:CoGetClassObject no class object {f50b3f13-19c4-11cf-aa9a-02608c9baba2} could be created for context 0x1
err:ole:CoGetClassObject class {9bc1b781-85e3-11d2-98d0-0080c84e9c39} not registered
err:ole:CoGetClassObject no class object {9bc1b781-85e3-11d2-98d0-0080c84e9c39} could be created for context 0x1
err:ole:CoGetClassObject class {dd1c057a-fe99-477c-835f-3a89ef577c6f} not registered
err:ole:CoGetClassObject no class object {dd1c057a-fe99-477c-835f-3a89ef577c6f} could be created for context 0x1
err:ole:CoGetClassObject class {f8904f1f-0371-4471-8866-90e6281abdb6} not registered
err:ole:CoGetClassObject no class object {f8904f1f-0371-4471-8866-90e6281abdb6} could be created for context 0x1
err:ole:CoGetClassObject class {238d0f23-5dc9-45a6-9be2-666160c324dd} not registered
err:ole:CoGetClassObject no class object {238d0f23-5dc9-45a6-9be2-666160c324dd} could be created for context 0x1
err:ole:CoGetClassObject class {feb50740-7bef-11ce-9bd9-0000e202599c} not registered
err:ole:CoGetClassObject no class object {feb50740-7bef-11ce-9bd9-0000e202599c} could be created for context 0x1
err:ole:CoGetClassObject class {cb51efc2-40d6-11d3-b265-00a0c9a3a56f} not registered
err:ole:CoGetClassObject no class object {cb51efc2-40d6-11d3-b265-00a0c9a3a56f} could be created for context 0x1
err:ole:CoGetClassObject class {301056d0-6dff-11d2-9eeb-006008039e37} not registered
err:ole:CoGetClassObject no class object {301056d0-6dff-11d2-9eeb-006008039e37} could be created for context 0x1
err:ole:CoGetClassObject class {64697678-0000-0010-8000-00aa00389b71} not registered
err:ole:CoGetClassObject no class object {64697678-0000-0010-8000-00aa00389b71} could be created for context 0x1
err:ole:CoGetClassObject class {04fe9017-f873-410e-871e-ab91661a4ef7} not registered
err:ole:CoGetClassObject no class object {04fe9017-f873-410e-871e-ab91661a4ef7} could be created for context 0x1
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:quartz:GetClassMediaFile Media class not found
err:quartz:GraphBuilder_AddSourceFilter Load (80004005)
Segmentation fault (core dumped)

```
So, any suggestions on how to fix these errors???

---

