---
title: "PHP CLI vs. Apache Module"
date: 2007-04-11
forum: General Help
---

### Post by xela321 on 2007-04-11
Just curious...

I have the following PHP script:

[PHP]
<?

$out = some array;
echo json_encode($out);

?>
[/PHP]

When I run the script with the command line interpreter: 'php script.php', it properly outputs the JSON-encoded representation of $out.

However, when I visit that script on the webserver, it kicks out an error that json_encode() is an undefined function.

Any ideas?

---

### Post by xela321 on 2007-04-11
nevermind.

I forgot to restart apache after installing php5-json

:o

---

