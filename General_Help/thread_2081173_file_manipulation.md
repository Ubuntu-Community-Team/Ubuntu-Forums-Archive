---
title: "file manipulation"
date: 2012-11-06
forum: General Help
---

### Post by Herbon on 2012-11-06
Problem: I ran the following command, from the wrong dir

>  find ./ -iname "*.avi" -exec mv '( )'  /home/SillyNubee/.gvfs/"mylibrary on X.X.X.X"/Network_Media_Video/Which located and moved the all of the ".avi" files from their individual folders. I can just simply delete the empty folders with 
> find . -depth -type d -empty -exec rmdir -v ( ) \;But how do I move similar named files into one folder ie "ITCrowdSE101", "ITCrowdSE111" into "ITCrowdSE1" Folder.

Thanks

---

### Post by steeldriver on 2012-11-06
Basically you can write a 'for' loop in bash that generates a dir name based on the file name (i.e. pattern substitution) and moves the file to that dir - HOWEVER you will need to define EXACTLY what you want to do - what is the format of the filenames? Do the season directories already exist? Is the episode number always exactly 2 digits and the season always exactly 1 digit for example?

---

### Post by SlugSlug on 2012-11-06
mv ITCrowdSE1* ITCrowdSE1/

---

### Post by nothingspecial on 2012-11-06
Could be worse, I once moved every single file, from every single folder recursively up to $HOME

One should be very careful with find

---

### Post by Herbon on 2012-11-06
> **steeldriver said:**
> Basically you can write a 'for' loop in bash that generates a dir name based on the file name (i.e. pattern substitution) and moves the file to that dir - HOWEVER you will need to define EXACTLY what you want to do - what is the format of the filenames? 

There are is no format of the filenames, some are named "ITCrowdSE101" or Sanford .and.son. or 10.Carol. Its a mix of different naming. 

>  Do the season directories already exist?

Yep there empty now :(

>  Is the episode number always exactly 2 digits and the season always exactly 1 digit for example?

No, never gotten around to do that. I guess I will now.

As for the "for" loop. Are you referring to...............

[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

??

---

### Post by steeldriver on 2012-11-06
Well if you have the dirs, you could loop  over *those* and find all the files with a base name equal to the dir name - something like

```

$ shopt -s nullglob
$ for dir in test/*/; do base="${dir%/}"; for file in "$base"*.avi; do echo mv "$file" "$dir"; done; done
mv test/ITCrowdSE101.avi test/ITCrowdSE1/
mv test/ITCrowdSE102.avi test/ITCrowdSE1/
mv test/ITCrowdSE103.avi test/ITCrowdSE1/
mv test/ITCrowdSE104.avi test/ITCrowdSE1/
mv test/ITCrowdSE105.avi test/ITCrowdSE1/
mv test/ITCrowdSE106.avi test/ITCrowdSE1/
mv test/ITCrowdSE107.avi test/ITCrowdSE1/
mv test/ITCrowdSE108.avi test/ITCrowdSE1/
mv test/ITCrowdSE109.avi test/ITCrowdSE1/
mv test/ITCrowdSE110.avi test/ITCrowdSE1/
mv test/ITCrowdSE111.avi test/ITCrowdSE1/
mv test/ITCrowdSE112.avi test/ITCrowdSE1/
mv test/Sanford .and.son.01.avi test/Sanford .and.son./
mv test/Sanford .and.son.02.avi test/Sanford .and.son./
mv test/Sanford .and.son.03.avi test/Sanford .and.son./
mv test/Sanford .and.son.04.avi test/Sanford .and.son./
mv test/Sanford .and.son.05.avi test/Sanford .and.son./
mv test/Sanford .and.son.06.avi test/Sanford .and.son./
mv test/Sanford .and.son.07.avi test/Sanford .and.son./
mv test/Sanford .and.son.08.avi test/Sanford .and.son./
mv test/Sanford .and.son.09.avi test/Sanford .and.son./
mv test/Sanford .and.son.10.avi test/Sanford .and.son./
mv test/Sanford .and.son.11.avi test/Sanford .and.son./
mv test/Sanford .and.son.12.avi test/Sanford .and.son./

```

(the 'echo' means it does not actually execute the move command - it's just printing what it would do)

---

### Post by Herbon on 2012-11-08
Thanks again!!

---

### Post by Herbon on 2012-11-08
> **nothingspecial said:**
> Could be worse, I once moved every single file, from every single folder recursively up to $HOME

One should be very careful with find

True

---

