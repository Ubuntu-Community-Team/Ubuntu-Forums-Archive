---
title: "php execution of mysql fails sometimes"
date: 2022-02-13
forum: General Help
---

### Post by pbeau on 2022-02-13
Hi

I am migrating a windows wamp server to ubuntu xampp. This was once, a long time ago a xampp server and now returning!
 This is all latest versions (I presume) as I installed using apt after update  in the previous week.

This code, when run simply stops... no error no nothing after the 'echo $query. That is to say, the mysql statement simply stops the execution. No error processing and no resulting error.



$query = "select * from assets";	if ($searchterm != '')
		{
		$query = $query." where Item like '%".$searchterm."%'";
		}
		
	}
	echo $query;
	$result = mysqli_query($db, $query);
	echo 'result = '.$result;
	if (!$result) 
	    	{
		echo ((is_object($GLOBALS["___mysqli_ston"])) ? mysqli_error($GLOBALS["___mysqli_ston"]) : (($___mysqli_res = mysqli_connect_error()) ? $___mysqli_res : false));
		exit;	
		}
	$numrows = @mysqli_num_rows($query);


It is not a general mysql or php error as this is executed as expected in the procedure that calls this one:

$query = "select distinct Category from assets";$result = @mysqli_query($GLOBALS["___mysqli_ston"], $query);
while ($Row = mysqli_fetch_array($result))
{
echo '<option value="'.$Row['Category'].'">'.$Row['Category'].'</option>';
}


the only thing I can find in the logs is:
2022-02-12 11:01:46 6 [Warning] InnoDB: Table mysql/innodb_table_stats has length mismatch in the column name table_name.  Please run mysql_upgrade
2022-02-12 11:01:46 6 [Warning] InnoDB: Table mysql/innodb_index_stats has length mismatch in the column name table_name.  Please run mysql_upgrade

however, running mysql_update says that is is depreciated and the upgrade is automatic.

I'm stuck. Can someone please point me in the right direction please?

Many thanks

P

---

### Post by pbeau on 2022-02-13
btw, I have restarted the server a number of times

---

### Post by norobro on 2022-02-13
Please edit your post and add code tags.

Is that all of your code? Just wondering if you have established a database connection.```
[COLOR=#0000BB][FONT=&amp]$db [/FONT][/COLOR][COLOR=#007700][FONT=&amp]= [/FONT][/COLOR][COLOR=#0000BB][FONT=&amp]mysqli_connect[/FONT][/COLOR][COLOR=#007700][FONT=&amp]([/FONT][/COLOR][COLOR=#DD0000][FONT=&amp]"server"[/FONT][/COLOR][COLOR=#007700][FONT=&amp], [/FONT][/COLOR][COLOR=#DD0000][FONT=&amp]"user"[/FONT][/COLOR][COLOR=#007700][FONT=&amp], [/FONT][/COLOR][COLOR=#DD0000][FONT=&amp]"password"[/FONT][/COLOR][COLOR=#007700][FONT=&amp], [/FONT][/COLOR][COLOR=#DD0000][FONT=&amp]"database"[/FONT][/COLOR][COLOR=#007700][FONT=&amp]);[/FONT][/COLOR]
```

---

### Post by pbeau on 2022-02-13
Yes

The connection is established ... at least it executes with no error. as mentioned a previous mysql instruction completes OK.

---

### Post by norobro on 2022-02-13
Sorry, I missed that in the jumble of code. I applied php code tags and cleaned up the formatting a little. 

There is a stray closing brace. That's all I've got. Maybe someone else will be able to help.

> **pbeau said:**
> [PHP]$query = "select * from assets";    
if ($searchterm != '')
{
    $query = $query." where Item like '%".$searchterm."%'";
}
        
    }  // <-- Here
echo $query;
$result = mysqli_query($db, $query);
echo 'result = '.$result;
if (!$result) 
{
    echo ((is_object($GLOBALS["___mysqli_ston"])) ? mysqli_error($GLOBALS["___mysqli_ston"]) : (($___mysqli_res = mysqli_connect_error()) ? $___mysqli_res : false));
    exit;    
}
$numrows = @mysqli_num_rows($query);
[/PHP]

It is not a general mysql or php error as this is executed as expected in the procedure that calls this one:

[PHP]$query = "select distinct Category from assets";
$result = @mysqli_query($GLOBALS["___mysqli_ston"], $query);
while ($Row = mysqli_fetch_array($result))
{
    echo '<option value="'.$Row['Category'].'">'.$Row['Category'].'</option>';
}
[/PHP]

---

### Post by pbeau on 2022-02-14
Thanks for the response. I posted an extract ... in the code the braces all have partners. If they didn't, php would throw an error wouldn't it?
It seems the mysql log is telling me what the problem is and even offers a solution ... but it doesn't work. And that is where I am stuck.

Regs

P

---

### Post by pbeau on 2022-02-17
Hi

I solved much of the problem by enabling the error messages. I did not know they wer disabled by default. for the time being, this at the top of the file helped:
error_reporting(E_ALL);
ini_set('display_errors', 1);

Once the rror was displayed, it became easier to solv the prob.

Regards

---

