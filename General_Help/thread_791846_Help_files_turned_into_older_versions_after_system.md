---
title: "Help: files turned into older versions after system crash"
date: 2008-05-12
forum: General Help
---

### Post by danimatielo on 2008-05-12
Hello, all

I have been using Ubuntu Feisty and today I was working on a report  using OpenOffice and the system suddenly crashed. I managed to save the files before re-start, but when the system started again, the files are seems like I haven't updated them in the last 2 days! And I have done a lot of work.

When I check for the Recent Updates, it points me to the file, but an older version, not my most recent ones. I have the feeling that it has recovered to an image of the system, but the problem is that I need the recent version.

Is there any place or a way to recover this file? (Disk image, hidden file, I don't know)

Any help is really appreciated.

Thank you in advance,

Dani

---

### Post by pytheas22 on 2008-05-12
Please change to the directory in which your file was being saved--by default this should be /home/YOUR-USER-NAME/Documents, but it could be anything else that you chose.  Then post the output of the ls -al command for that directory.  For example, if your user name is dani and the file is saved in the Documents directory, run:

```
cd /home/dani/Documents
ls -al
```

and then please copy and paste the output here.

There may be something to work with based on that command.

---

### Post by bingoUV on 2008-05-12
Can you post the output of 
```

mount

```

---

### Post by danimatielo on 2008-05-12
> **pytheas22 said:**
> Please change to the directory in which your file was being saved--by default this should be /home/YOUR-USER-NAME/Documents, but it could be anything else that you chose.  Then post the output of the ls -al command for that directory.  For example, if your user name is dani and the file is saved in the Documents directory, run:

```
cd /home/dani/Documents
ls -al
```

and then please copy and paste the output here.

There may be something to work with based on that command.

Thank you for your help. Here is the output:

nan@nan-laptop://home/nan/Desktop/Documents/ponline$ ls -al
total 21068
drwxr-xr-x 2 nan nan    4096 2008-05-12 20:52 .
drwxr-xr-x 7 nan nan    4096 2008-05-12 21:54 ..
-rw-r--r-- 1 nan nan    1038 2008-04-26 23:34 Anos de Estudo SP PNAD.csv
-rw-r--r-- 1 nan nan  566762 2008-04-15 18:40 apresentacao_ponline2007.odp
-rw-r--r-- 1 nan nan  110592 2008-04-30 18:07 cruzamento_avaliacao.xls
-rw------- 1 nan nan  433164 2008-04-27 01:38 destaques-governo-eletronico-tic-2007CGI.pdf
-rw-r--r-- 1 nan nan  131369 2008-04-29 20:35 digitaldivideINTERNET.jpg
-rw-r--r-- 1 nan nan  129553 2008-04-29 20:34 digitaldivideMOBILEjpg
-rw-r--r-- 1 nan nan  129553 2008-04-29 20:35 digitaldivideMOBILE.jpg
-rw-r--r-- 1 nan nan    1602 2008-04-26 23:23 Distribuicao Faixas Etárias SP Pnad.csv
-rw-r--r-- 1 nan nan    1334 2008-04-26 23:46 Escolaridade SP Pnad.csv
-rw------- 1 nan nan   90872 2008-04-27 01:07 Eurostat.pdf
-rw-r--r-- 1 nan nan     450 2008-04-26 23:24 Genero SP Pnad.csv
-rw-r--r-- 1 nan nan   16988 2008-04-16 04:00 IBGE e PNAD.ods
-rw-r--r-- 1 nan nan   12793 2008-04-15 23:55 índice.odt
-rw-r--r-- 1 nan nan   98304 2008-04-15 23:55 índice ponline2007.doc
-rw-r--r-- 1 nan nan   21798 2008-04-30 12:39 internet stats.ods
-rw-r--r-- 1 nan nan    3300 2008-04-27 02:29 ipeadata_1502872859.csv
-rw-r--r-- 1 nan nan    2661 2008-04-27 02:31 ipeadata_1502995437.csv
-rw-r--r-- 1 nan nan    9288 2008-04-27 02:32 ipeadata_1503065109.csv
-rw-r--r-- 1 nan nan   62170 2008-04-29 22:37 perfil EGOV Poupatempo.odp
-rw------- 1 nan nan  473111 2008-04-27 01:16 PIP_Teens_Social_Media_Final-PEW.pdf
-rw-r--r-- 1 nan nan  370934 2008-04-13 20:17 planilha 3.ods
-rw-r--r-- 1 nan nan  827906 2008-04-16 03:53 planilha de trabalho2.ods
-rw-r--r-- 1 nan nan 1037824 2008-04-26 19:03 planilha de trabalho2.xls
-rw-r--r-- 1 nan nan       0 2008-04-13 20:14 planilha de trabalho3.ods
-rw-r--r-- 1 nan nan  448018 2008-04-11 19:54 planilha de trabalho.ods
-rw-r--r-- 1 nan nan  952708 2008-04-29 01:40 planilha de trabalho PONLINE2.ods
-rw-r--r-- 1 nan nan 1039360 2008-04-30 20:48 planilha de trabalho PONLINE3.xls
-rw-r--r-- 1 nan nan 1093038 2008-05-12 21:07 planilha de trabalho PONLINE.ods
-rw-r--r-- 1 nan nan 1037824 2008-04-26 19:04 planilha de trabalho PONLINE.xls
-rw-r--r-- 1 nan nan  183577 2008-04-05 23:43 ponline2007-1.ods
-rw-r--r-- 1 nan nan  529884 2008-04-29 22:46 ponline2007-2.odp
-rw-r--r-- 1 nan nan  504320 2008-04-16 14:47 ponline 2007 .doc
-rw-r--r-- 1 nan nan   84364 2008-04-06 00:28 ponline2007-frequenciaAcessaConhecemInfo.ods
-rw-r--r-- 1 nan nan   51161 2008-04-06 00:25 ponline2007-frequenciaCel.ods
-rw-r--r-- 1 nan nan   45195 2008-04-06 00:24 ponline2007-frequenciaOpiniaoComunicacao.ods
-rw-r--r-- 1 nan nan   70200 2008-04-06 00:23 ponline2007-frequenciaUsuário.ods
-rw-r--r-- 1 nan nan  184411 2008-04-06 00:22 ponline2007-multipla escolha.ods
-rw-r--r-- 1 nan nan  821191 2008-04-30 19:18 ponline2007.odp
-rw-r--r-- 1 nan nan  523715 2008-05-10 18:13 ponline 2007 .odt
-rw-r--r-- 1 nan nan   62306 2008-04-11 20:08 ponline2007-portal.ods
-rw-r--r-- 1 nan nan   47883 2008-04-06 19:18 ponline2007-usuário.ods
-rw-r--r-- 1 nan nan  962698 2008-05-06 12:51 ponline2007v5-1.odp
-rw-r--r-- 1 nan nan 1118720 2008-05-06 12:52 ponline2007v5-1.ppt
-rw-r--r-- 1 nan nan 1044480 2008-05-11 18:44 ponline 2007 v6.doc
-rw-r--r-- 1 nan nan  899100 2008-05-12 21:19 ponline2007v6.odp
-rw-r--r-- 1 nan nan 1085440 2008-05-11 16:27 ponline2007v6.ppt
-rw-r--r-- 1 nan nan 1048064 2008-05-12 19:56 ponline 2007 v7.doc
-rw-r--r-- 1 nan nan  629980 2008-05-12 20:46 ponline 2007 v7.odt
-rw-r--r-- 1 nan nan  630367 2008-05-12 22:07 ponline 2007 v8.odt
-rw-r--r-- 1 nan nan   80659 2008-04-11 20:08 ponline2007-vidapessoal.ods
-rw-r--r-- 1 nan nan  172032 2008-04-24 19:53 @Q_12.xls
-rw-r--r-- 1 nan nan  110451 2008-04-27 00:14 Redes Sociais Mundo
-rw-r--r-- 1 nan nan  218728 2008-04-16 15:12 Relatório Ponline 2007.odt
-rw-r--r-- 1 nan nan     844 2008-04-26 23:53 Rendimento Familiar SP Pnad.csv
-rw-r--r-- 1 nan nan  919499 2008-04-30 18:56 servicos egov padrao cgi.ods
-rw-r--r-- 1 nan nan  110451 2008-04-29 11:41 socialnetworkingmap.gif
-rw-r--r-- 1 nan nan   35328 2008-04-27 02:04 UsoTIC-core indicators.xls

My file is listed, which is ponline 2007 v7.doc, but the version that it shows is an older one.

---

### Post by pytheas22 on 2008-05-12
It doesn't look like there are any hidden or backup files in that directory, unfortunately.  Are you sure that the file you're looking for is ponline 2007 v7.doc, and not ponline 2007 v7.odt, which also exists--maybe you saved it last in .odt format but didn't realize it.

By the way, how did you save the "save the files before re-start," and what exactly happened when the system crashed?  Did it just freeze altogether, did only X crash, could you move the mouse but not click anything...?

When I get home to my Ubuntu box (I'm at work on XP now...) I'll try to take a look around my file system and see where else the file could be.  OpenOffice usually does a really good job of auto-saving backups, I'm just not sure where it puts them.

---

### Post by pytheas22 on 2008-05-12
Inside my home folder is a directory called '.openoffice.org2/user' and inside that is one called 'backup.'  Is your file there?

---

### Post by bingoUV on 2008-05-13
Posting the output of the following will help us confirm whether any unsafe journal options have not been selected to mount your device.
```

mount 

```

---

