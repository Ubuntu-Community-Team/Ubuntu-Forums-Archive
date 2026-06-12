---
title: "BASH scripting Multiple Variables"
date: 2013-02-24
forum: General Help
---

### Post by gachnar on 2013-02-24
I'm working on a script that will have a few goals. 


[LIST=1]
[*]That it will read all attachments from a MKV file and get the attachment ID and store on a variable
[*]That it will get the name from the attachment and store in a second variable
[*]That it will check attachment name to see if the TTF file already exists in my font cache directory. If so, do nothing, if not, extract and move the file to my cache directory.
[/LIST]

I don't want to constantly extract all the fonts if they already exist, but I am by no means a BASH guru and am trying to expand my skills. Can someone help? Attached below is my relevant scriptlet.


```

for f in *.mkv
do
  attachments=$(mkvmerge --identify TEST.mkv | grep Attachment | awk -F " " '{print $3}' | sed 's/://g' )
  fontname=$(mkvmerge --identify TEST.mkv | grep Attachment | awk -F "'" '{print $4}')

  #Here is the part that I can't figure out. Let me know what you think

  for font in $attachments && for name in $fontname;
    do
      echo 'Extract attachment $font from $f'
      mkvextract attachments "$f" $attachments
      echo "$fontname"
      sleep 30
  done
done

sudo fc-cache -fv



```

---

### Post by Vaphell on 2013-02-24
```
#!/bin/bash

for f in *.mkv
do
  while read a_id font
  do
    echo "Extract attachment #$a_id ($font) from $f"
    mkvextract attachments "$f" "$a_id"
  done < <( mkvmerge --identify "$f" | sed -rn "/Attachment/ s/.*([0-9]+):.*'(.*)'/\1 \2/p" )
done 
```

---

### Post by gachnar on 2013-02-25
Thanks for that. I have had a long day and will test that here shortly and report back.

---

