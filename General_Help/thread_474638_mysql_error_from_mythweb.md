---
title: "mysql error from mythweb"
date: 2007-06-15
forum: General Help
---

### Post by Scorpuk on 2007-06-15
I am running mythweb on my server and I get the following error in my browser and was wondering if anyone can shed some light on the problem?



> Fatal error: Call to a member function query() on a non-object in /usr/share/mythtv/mythweb/includes/session.php on line 60


Line 60 is as follows:

```
$db->query('REPLACE INTO mythweb_sessions (id, modified, data) VALUES(?,NULL,?)',
```


And the full function it resides in is:

```
/**
 * Write the session data to the database
/**/
    function sess_write($id, $data) {
        global $db;
        if (!empty($_SERVER['REMOTE_USER']))
            $id = 'user:'.$_SERVER['REMOTE_USER'];
        $db->query('REPLACE INTO mythweb_sessions (id, modified, data) VALUES(?,NULL,?)',
                   $id, $data);
        if (!$db->affected_rows())
            return false;
    // Return true
        return true;
    }
```

Fortunately it does not stop mythweb from working. 


Tnx in advance

---

### Post by dotduke on 2007-06-17
I had the same problem after my upgrade from Edgy to Feisty.
I could not store any session data.


I apllied the following hack to _init.php_ en _session.php_ both in the mythweb/includes-directory.

1 . Comment out the server variables in _init.php_ like this:
( while you&#341;e in there copy the relevant code )

```
// We don't need these security risks hanging around taking up memory.
//    unset($_SERVER['db_name'],
//          $_SERVER['db_login'],
//          $_SERVER['db_password'],
//  
```

2. Modify the function sess_write in _session.php_:

```

function sess_write($id, $data) {
        global $db;
        if (!empty($_SERVER['REMOTE_USER']))
            $id = 'user:'.$_SERVER['REMOTE_USER'];
[B]
      // Connect to the database ( copied form init.php )
        if (!is_object($db)) {
        $db = Database::connect($_SERVER['db_name'],
                                $_SERVER['db_login'],
                                $_SERVER['db_password'],
                                $_SERVER['db_server'],
                                NULL, 'mysql');[/B]

[B]// We don't need these security risks hanging around taking up memory. ( copied form init.php )
   unset($_SERVER['db_name'],
        $_SERVER['db_login'],
        $_SERVER['db_password'],
        $_SERVER['db_server']);

        }[/B]

	[B]// Access denied -- probably means that there is no database  ( copied form init.php )
  	if ($db->errno == 1045) {
    	   tailored_error('db_access_denied');
    	}[/B]

        $db->query('REPLACE INTO mythweb_sessions (id, modified, data) VALUES(?,NULL,?)',
                   $id, $data);
        if (!$db->affected_rows())
            return false;
        // Return true
        return true;
    }
```

As you can see I copied these functions from init.php to session.php.

It worked for me, although I hope this will be fixed at a more elegant way in Gutsy. ;)

---

### Post by Scorpuk on 2007-06-27
Cheers dotduke.

Updated the two php files and now I don't get the error message any more.

---

### Post by dannyboy79 on 2007-06-27
I jhave this same errror, I am curious, what do you mean when you say you can't save any session data? Because I am at work right now, tunneled into my server with putty, and am viewing mythweb thru the tunnel. I just chose to record a new show, and it did update everything by the looks of it. So what am I missing here? thanks in advance

---

### Post by drifting on 2007-07-01
Thanks dotduke ! Just saved me hours of searching through google.

Not sure what you changed, but it solved the error for me.

Paul.

---

### Post by Virus on 2007-07-30
I only have one thing to say about this "Brilliant" :p

---

