---
title: "Mass edit files command line"
date: 2013-02-11
forum: General Help
---

### Post by bigbankclub on 2013-02-11
Hey I have a project to do. I have 15 blank .html files. I need to figure a way to place the same text hello in each one. Is there a quick and dirty way? Not using a script but some other way that would work?:(

---

### Post by Bufeu on 2013-02-11
[http://rushi.wordpress.com/2008/08/05/find-replace-across-multiple-files-in-linux/](http://rushi.wordpress.com/2008/08/05/find-replace-across-multiple-files-in-linux/)

---

### Post by schragge on 2013-02-11
sed or awk?

---

### Post by steeldriver on 2013-02-11
What do you mean by 'blank html'? is there an existing html tag that you are trying to insert a text field into, or are they are actual zero length files?

If the latter you could maybe do something like

```
$ tee *.html < <(cat <<EOF
your
HTML
goes
here
EOF
)

```

---

### Post by schragge on 2013-02-12
*@steeldriver*. Just wondering, isn't it the same as
```

tee *.html <<EOF
your
HTML
goes
here
EOF

```:?:

---

### Post by HermanAB on 2013-02-12
Since they are all the same, the better way is to make 14 simlinks...

---

### Post by steeldriver on 2013-02-12
> **schragge said:**
> *@steeldriver*. Just wondering, isn't it the same as
```

tee *.html <<EOF
your
HTML
goes
here
EOF

```:?:

doh! you're right - I overcomplicated it

---

