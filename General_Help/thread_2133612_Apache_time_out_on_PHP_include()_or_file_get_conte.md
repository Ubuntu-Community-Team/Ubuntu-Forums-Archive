---
title: "Apache time out on PHP include() or file_get_contents() through HTTP"
date: 2013-04-08
forum: General Help
---

### Post by JackTheKnife on 2013-04-08
I have a problem with ExpressionEngine2 after moving from an old server to a new one. Simple test code to reproduce that issue:

[PHP]<?php 
        $protocol = strpos(strtolower($_SERVER['SERVER_PROTOCOL']),'https') === FALSE ? 'http' : 'https';
        $host = $_SERVER['HTTP_HOST'];
        include($protocol . '://' . $host . '/header.html'); 
?>
    <p> Main text...</p>
<?php
        include($protocol . '://' . $host . '/footer.html'); 
?>[/PHP]


Where header.html looks like


```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Untitled Document</title>
</head>
<body>
```


and footer.html looks like:


```
</body>
</html>

```

Creates Apache time out:


```
Warning: include(http://www.domain.com/header.html) [function.include]: failed to open stream: Connection timed out in /home/domain/public_html/test/index.php on line 5

Warning: include() [function.include]: Failed opening 'http://www.domain.com/header.html' for inclusion (include_path='.:/usr/lib/php:/usr/local/lib/php') in /home/domain/public_html/test/index.php on line 5

Main text...

Warning: include(http://www.domain.com/footer.html) [function.include]: failed to open stream: Connection timed out in /home/domain/public_html/test/index.php on line 12

Warning: include() [function.include]: Failed opening 'http://www.domain.com/footer.html' for inclusion (include_path='.:/usr/lib/php:/usr/local/lib/php') in /home/domain/public_html/test/index.php on line 12

```

Same problem when I use file_get_contents() instead include().

Any clue what can be wrong with Apache or PHP configuration?

Thanks

---

