---
title: "Determine if each page in PDF has the same height"
date: 2014-02-02
forum: General Help
---

### Post by shaneod on 2014-02-02
I use the following code to convert swf books to pdf:
swftopdf () {
```
swftopdf () {
if [ ! -f "$1.pdf" ]; then
    wget "http://content.yudu.com/android/dJcuwVV99lEgqWoc/content/$1.high";
    mimetype=$(file $1.high --mime-type);
    if [ "$mimetype" == "$1.high: application/x-shockwave-flash" ]; then
        swfrender -Y 2500 "$1.high" -o "$1.png"; convert "$1.png" "$1.pdf";
    else
        convert "$1.high[x2500]" "$1.pdf"; fi; rm -rf $1.high; rm -rf $1.png;
    fi;
};
for i in {1..244}; do
    while [ ! -f "$i.pdf" ]; do
        swftopdf $i;
    done;
done;
filelist=$(ls|sort -n);
pdftk $filelist cat output '/home/shane/Desktop/Complete Ebooks/Secondary Level/Leaving Cert/Folens/Othello.pdf' compress; rm -rf *.pdf
```
Rarely, the .high file would be a jpg rather than a swf, hence why there's the else convert "$i1.high[x2500]" segment. However, I didn't initially have [x2500] written there.
So, what I'm wondering is, rather than deleting all the books I've already converted, **is there any way of figuring out if any of the pages has a height which differs to 2500 in the large pdf** (the .high's, .png's and individual .pdf's are already deleted), so I can then delete and reconvert that book, so that the jpg pages have a height of 2500 too?
Thanks


Also, if anyone knows a less conveluted way of doing this, I'd appreciate it if they told me it :)


If you need an example of 1 page being a .swf, and another being a .jpg, for explanatory purposes:
[http://content.yudu.com/android/dJcuwVV99lEgqWoc/content/1.high](http://content.yudu.com/android/dJcuwVV99lEgqWoc/content/1.high) - swf
[http://content.yudu.com/android/dJcuwVV99lEgqWoc/content/2.high](http://content.yudu.com/android/dJcuwVV99lEgqWoc/content/2.high) - jpg


EDIT: Solved [here]("http://stackoverflow.com/a/21528409/1943638") thanks to leu.

---

