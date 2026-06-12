---
title: "&quot;save as&quot; in firefox from bash script"
date: 2013-08-21
forum: General Help
---

### Post by er-schuster on 2013-08-21
I want to save the content of a dynamic generated webpage in a text file for further processing from a bash script under Linux. I`m not interested in the source code; all I want is the output of that page to be saved locally (correspondes to Strg+S in firefox). I tried wget, curl... and all that stuff - but this saved only the static part of the page.
  Is there a simple way to save this in a file from command line using firefox or any other browser ?

---

### Post by hakermania on 2013-08-21
You may try downloading the entire webpage using wget:

```
wget --recursive --no-clobber --page-requisites --html-extension --convert-links --restrict-file-names=windows --domains example.com --no-parent http://yourwebsite.com
```

Taken from: [http://janezurevc.name/download-entire-web-page-using-wget](http://janezurevc.name/download-entire-web-page-using-wget)

---

