---
title: "deleting default folders in Home makes mess"
date: 2024-01-23
forum: General Help
---

### Post by ishmael3 on 2024-01-23
On a recent install of 22.04 I deleted (moved to trash) several of the folders in the Home directory -- specifically: Documents, Music, Videos. I then created several new ones -- like: Finance. 

In past Ubuntu versions I have done this with seeming impunity. But now I am wondering if I broke something. 

On next restart, in the Home directory, I found broken links pointing to the deleted folders -- I deleted the broken links supposing they were no longer useful. And then a folder that I didn't delete -- Downloads -- disappeared by itself, leaving behind another broken link. So then I was concerned.

Some research tells me this probably has something to do with "xdg" which I'd never heard of before now. I find that 22.04 has several xdg-packages installed. 

So, question: Is there a way to clean this up? One help site says that running **xdg-user-dirs-update **will recreate the full suite of localized directories (not sure if that's system or for each user). Not sure what effect it might have on existing broken links or on new folders that I have already created in Home (using simply rt-click > New Folder).

Another question: How* should* I have deleted and added directories within Home to begin with?

---

