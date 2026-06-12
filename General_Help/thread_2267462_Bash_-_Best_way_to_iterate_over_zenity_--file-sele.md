---
title: "Bash - Best way to iterate over zenity --file-selection output"
date: 2015-03-01
forum: General Help
---

### Post by CaptainMark on 2015-03-01
I'm writing a script that I would like to iterate a for loop over the output from a zenity --file-selection multiple file command but I'm having a bit of trouble getting the exact method correct, I'm having delimiter issues and I keep getting the for loop iterating over the wrong file names. Here is the zenity command ```
zenity \
                --title="Sort Episodes" \
                --file-selection \
                --multiple
```So pretty basic there, zenity has the --separator="" option and presumably that would be useful but again I cant figure out how to nest this into a for loop, I tried doing this hoping it would work```

while read video ; do
echo -e "$video\n"
sleep 1
done< <(zenity \
                --title="Sort Episodes" \
                --file-selection \
                --multiple \

```
Obviously in this test I was hoping I would get one video name echoed per second but I just get the whole string of files printed in one block, by default zenity uses a pipe | character as a separator so how can I use a pipe character as a delimiter in the for loop, or how can I get zenity to use a null character as a separator.

I'm lost, please help.

Regards
Mark

---

