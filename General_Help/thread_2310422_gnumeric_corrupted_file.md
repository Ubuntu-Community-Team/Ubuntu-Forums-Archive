---
title: "gnumeric corrupted file"
date: 2016-01-19
forum: General Help
---

### Post by Azzurra on 2016-01-19
Hello everyone!
I have a very crushing issue! I am used to GNUMERIC to process my data. The last time I used it I saved my .gnumeric file as usual. When I tried to open it again everything was gone (sheets, numbers, graphs, ...) but some strange types in one single sheet. I tried to open the .gnumeric file with libre office but I was not able since it was not recognising the input. Now, what is going on????????????????? I did not find anything about this topic on specific forums so...help me PLEASEEEEEEEEEEEE!!!!!!!!!!!!

Thanks you,

Cheers,

Azzurra.

---

### Post by jbrefort on 2016-01-20
Quite strange. Check the file type. If you use compressed files, rename to .numeric.gz and gunzip it. You should get a text (xml) file which you cans test with xmllint to see if it is valid.

Also, starting gnumeric from the command line might provide some error messages.

Hope this helps,
Jean

---

