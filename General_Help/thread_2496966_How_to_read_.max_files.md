---
title: "How to read .max files"
date: 2024-04-18
forum: General Help
---

### Post by satimis on 2024-04-18
Hi all,

I found .max files on my old database.  Please advise how can I read them.

Thanks

Regards

---

### Post by dragonfly41 on 2024-04-18
I have started using Recoll to index all my files on my Ubuntu 22.04 desktop.  Although on first pass it takes a long time to index the universe of files thereafter it is very useful. Update index from time to time as files are added, relocated, renamed. Blacklist paths you do not need.

I have looked at my index and I user Query field:  ext:max
This means ... " list all indexed files with extension [ext] = [max]". Hover mouse over Query field to see "cheat sheet". Examples of queries.

I see :

index.js
LICENSE
package.json
README.md

They spring from node.js it seems.

---

### Post by satimis on 2024-04-18
> **dragonfly41 said:**
> I have started using Recoll to index all my files on my Ubuntu 22.04 desktop.  Although on first pass it takes a long time to index the universe of files thereafter it is very useful. Update index from time to time as files are added, relocated, renamed. Blacklist paths you do not need.

I have looked at my index and I user Query field:  ext:max
This means ... " list all indexed files with extension [ext] = [max]". Hover mouse over Query field to see "cheat sheet". Examples of queries.

I see :

index.js
LICENSE
package.json
README.md

They spring from node.js it seems.
Hi,

Thanks for your reply.

.max is PaperPort document.  How to read it on Ubuntu?

Regards

---

### Post by HermanAB on 2024-04-19
cat, more, less, hexedit…

---

### Post by dragonfly41 on 2024-04-19
Much depends on _how many_ files to be previewed and commands then applied, file by file. I still maintain that Recoll is a very convenient tool to go through hundreds of archived files. I have found one *.max file which represents SageMath. But one click in Recoll index I can preview the content. It is the usual choice of GUI versus CLI. Leverage both in my thinking. Or in Recoll you can map MIME types to custom MIME type viewers including a  custom script as suggested which runs, cat, more, less, hexedit. Orchestrate desktop assets. I have no knowledge of PaperPort.

---

### Post by satimis on 2024-04-19
> **HermanAB said:**
> cat, more, less, hexedit…
$ cat file.max
only print out the codes

Regards

---

### Post by satimis on 2024-04-19
> **dragonfly41 said:**
> Much depends on _how many_ files to be previewed and commands then applied, file by file. I still maintain that Recoll is a very convenient tool to go through hundreds of archived files. I have found one *.max file which represents SageMath. But one click in Recoll index I can preview the content. It is the usual choice of GUI versus CLI. Leverage both in my thinking. Or in Recoll you can map MIME types to custom MIME type viewers including a  custom script as suggested which runs, cat, more, less, hexedit. Orchestrate desktop assets. I have no knowledge of PaperPort.
I just found 2~4 .max files on my database.  I expect to know their contents

Regards

---

### Post by dragonfly41 on 2024-04-19
As I wrote I have no knowledge of PaperPort. But a quick research shows this.

[https://support.hp.com/ph-en/document/bps01259](https://support.hp.com/ph-en/document/bps01259)

So should the question be "how to view Windows source *.max files in Ubuntu?"
And this surfaces.

[https://ubuntuforums.org/showthread.php?t=2143591](https://ubuntuforums.org/showthread.php?t=2143591)

[https://sourceforge.net/projects/maxview/](https://sourceforge.net/projects/maxview/)

If you are using Recoll (although you write you only have 2-4 *.max files, hardly a sole reason to leverage Recoll), you could set the Recoll GUI to open installed app "maxview" when you click on any indexed *.max file seen in Recoll. For example I have many (hundreds) CherryTree files with extension *.ctd indexed and I changed the mapping to launch cherrytree %f (open the indexed file in app cherrytree).  Or I could map to an XML editor XMLCopyEditor. Same mapping method applies to all extensions (MIME types). Often the Default Viewer setting needs to be customised (particularly so when different apps share the same MIME type.  For such scenario I map to a routing script which then opens the indexed file from a list of apps.


[Postscript]

PhotoRec mentions PaperPort in recovery options.

[https://www.bikechatforums.com/viewtopic.php?p=2390043](https://www.bikechatforums.com/viewtopic.php?p=2390043)

[https://cse.google.com/cse?cx=partner-pub-9753209298218671%3A1590919361&q=Paperport&oq=Paperport&gs_l=partner-generic.3...33116.37052.0.39089.0.0.0.0.0.0.0.0..0.0.csems%2Cnrl%3D10...0....1.34.partner-generic..0.0.0](https://cse.google.com/cse?cx=partner-pub-9753209298218671%3A1590919361&q=Paperport&oq=Paperport&gs_l=partner-generic.3...33116.37052.0.39089.0.0.0.0.0.0.0.0..0.0.csems%2Cnrl%3D10...0....1.34.partner-generic..0.0.0).

---

### Post by ActionParsnip on 2024-04-19
The . max file format was developed by Autodesk for the 3ds Max application. 3ds Max is a 3D modeling, animation, and rendering solution used to create 3D animation for game development, design visualization, feature film and television effects, and education.

Source: Google.

So...this nonsense:
[https://www.autodesk.com/support/technical/article/caas/tsarticles/ts/77DVRQ8wFRltRxWlSY4HVt.html](https://www.autodesk.com/support/technical/article/caas/tsarticles/ts/77DVRQ8wFRltRxWlSY4HVt.html)

May want to switch to an RPM based distribution if this is the main use (I don't know if this is right. I don't use stuff like this but my Google-fu is strong)

---

### Post by dragonfly41 on 2024-04-19
Crafting this prompt to AI assistant
"Which applications use .max extension and how can they be viewed in Ubuntu?"
leads to here ..
[https://github.com/sjg20/paperman](https://github.com/sjg20/paperman)

and possibly try importing into Blender.

---

### Post by phatton1 on 2024-04-19
Apparently 7zip can open them for viewing

---

### Post by satimis on 2024-04-19
> **phatton1 said:**
> Apparently 7zip can open them for viewing
Is it the '7zip' on REPO or 7zip for Windows?

I have installed 7zip on REPO but unable to start it reading .max file

There are websites online providing FREE service
1. convert .max file to .pdf 
or
2. reading .max file online.

But they need filling in my credit card detail.  I hesitate to proceed

---

### Post by dragonfly41 on 2024-04-19
I wouldn't.  As I listed, Blender is in Ubuntu repo and/or you can compile PaperMan.

However digging deeper Blender requires a conversion (if original 3DS Max is unavailable).

[https://blender.stackexchange.com/questions/14808/how-to-import-a-max-model-into-blender#:~:text=blend%20is%20Blender's%20native%20format,no%20way%20to%20import%20a%20](https://blender.stackexchange.com/questions/14808/how-to-import-a-max-model-into-blender#:~:text=blend%20is%20Blender's%20native%20format,no%20way%20to%20import%20a%20).

So perhaps try PaperMan first.

---

### Post by satimis on 2024-04-19
> **dragonfly41 said:**
> I wouldn't.  As I listed, Blender is in Ubuntu repo and/or you can compile PaperMan.

However digging deeper Blender requires a conversion (if original 3DS Max is unavailable).

[https://blender.stackexchange.com/questions/14808/how-to-import-a-max-model-into-blender#:~:text=blend%20is%20Blender's%20native%20format,no%20way%20to%20import%20a%20](https://blender.stackexchange.com/questions/14808/how-to-import-a-max-model-into-blender#:~:text=blend%20is%20Blender's%20native%20format,no%20way%20to%20import%20a%20).

So perhaps try PaperMan first.
I ran PaperPort long time ago on Windows.  It is now renamed as PaperMan under GitHub.  I'll try their forum later to see whether they can help.

---

### Post by dragonfly41 on 2024-04-19
This is an explanation of build process ..

[https://github.com/sjg20/paperman/issues/23](https://github.com/sjg20/paperman/issues/23)

---

### Post by him610 on 2024-04-19
Found this online...
> 
Opening . max files using 3ds Max compatible software
Blender is a free, open-source 3D creation suite that offers an alternative for working with . ...
Cinema 4D is a powerful and user-friendly 3D modeling, animation, and rendering software developed by Maxon.


---

### Post by Holger_Gehrke on 2024-04-19
The .max of 3ds max and the ones from Paperport are very unlikely to be even remotely similar. 3D Studio Max is (like blender) a program for creating three dimensional graphics and it's .max format is its native format for storing complete scenes including all kinds of effects. Paperport on the other hand is a program for scanning documents and keeping track of them - a document management program, which was for a time packed in with various scanners and similar devices. The reason for the '.max' extension is that an older version of the program went by the name of 'MaxMate'.

Holger

---

### Post by dragonfly41 on 2024-04-19
I found from using Recoll that multiple applications can share the same MIME type. Which can be confusing when mapping to viewers. For example Scribus *.sla can be viewed in XML editor. Likewise CherryTree and others like SVG.

---

