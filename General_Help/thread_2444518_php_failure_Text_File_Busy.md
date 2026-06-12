---
title: "php failure: Text File Busy"
date: 2020-05-31
forum: General Help
---

### Post by bilkay on 2020-05-31
In ubuntu 20.04, php 7.4, I have a php script in a remotely mounted directory (nfs). The server where the script resides is running php-7.4. On the server, the script runs until I open it for editing (and close it). Then forever after (it seems) the script fails with error: "/usr/bin/php: bad interpreter: Text file busy". The remote machine runs php-7.0, and the script runs under that whether or not it can run on the server. I checked lsof to see if the file is open and it's not listed.

Apparently, the only way to reset this is to reboot the server.

---

### Post by sdsurfer on 2020-06-01
This most likely means at the time you are calling the script, it is being ***executed***. PHP files after all are plain text files. I doubt there's a "forever" especially since you get nothing with lsof. My first guess would be something in the timing of your logic occurs while the "editing" is happening.

IMO I would try another way other than editing a running script. Move whatever you need to edit into a config file, edit that instead. If you absolutely must stick with this logic, open a copy, modify, resave, then rename. Even if you use a config file, operate on a copy and rename.

---

### Post by SeijiSensei on 2020-06-01
Make sure you have the opening and closing PHP tags in your script.  It should look like this:
```

#!/usr/bin/php 
<?php
PHP code here
?>

```

---

### Post by bilkay on 2020-06-01
This isn't something limited to php, it happens with bash scripts too. The good news is that it isn't "forever," it eventually clears.

---

### Post by sdsurfer on 2020-06-02
Closing tags are only necessary for inline code, a bad practice IMO (violates separation of concerns) and not required if it's the last output in the file.
```

<?php
echo "<p>This is some inlne PHP code.</p>";
?>

<p>This is some regular text output.</p>

<?php
echo "<p>And we're done.</p>";

```

---

### Post by bilkay on 2020-06-02
> **sdsurfer said:**
> This most likely means at the time you are calling the script, it is being ***executed***. PHP files after all are plain text files. I doubt there's a "forever" especially since you get nothing with lsof. My first guess would be something in the timing of your logic occurs while the "editing" is happening.

IMO I would try another way other than editing a running script. Move whatever you need to edit into a config file, edit that instead. If you absolutely must stick with this logic, open a copy, modify, resave, then rename. Even if you use a config file, operate on a copy and rename.

It just makes debugging scripts a little more complicated. It must be a "security" thing.

---

### Post by bilkay on 2020-06-03
> **sdsurfer said:**
> IMO I would try another way other than editing a running script. Move whatever you need to edit into a config file, edit that instead. If you absolutely must stick with this logic, open a copy, modify, resave, then rename. Even if you use a config file, operate on a copy and rename.

This doesn't solve the problem. I copied a script, edited the copy, then renamed it to the original name, and when I tried to run the script, it failed with the "Text file busy" error message.

---

### Post by SeijiSensei on 2020-06-03
We need to see the script, inside [noparse]```

```[/noparse] tags.

---

