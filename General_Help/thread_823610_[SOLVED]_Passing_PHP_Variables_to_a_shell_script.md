---
title: "[SOLVED] Passing PHP Variables to a shell script"
date: 2008-06-09
forum: General Help
---

### Post by tcpip4lyfe on 2008-06-09
First off, I'm not going to lie, I have very limited scripting skills.  Currently I have a postfix server running on a mysql database.  When I want to add a new user I have to create to user in the database and then create the user's mailbox by telneting to the mail server and manually sending him an email.  Bascially I want to automate the process so that when I set up the user, I can browse to a web page, put in the email address and password, and it will create the user in mysql and then send an email to that user to create the mail box.  Currently I have this working with a simple php script that creates the mysql entry and then calls an expect script to send the email to create the mailbox.  The code is as follows:

```

###Create_email.php
<html>
<head>
<title>Add New MySQL User</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>

<body>
<?
if(isset($_POST['add']))
{
**$username = $_POST['username'];**
$password = $_POST['password'];

mysql_connect ("localhost", "root", "rootpassword") or die ('Error: ' . mysql_error());
mysql_select_db ("mail");

$query = "INSERT INTO `users` ( `email` , `password` , `quota` )VALUES ('$username', ENCRYPT('$password'), NULL)";
mysql_query($query) or die('Error, insert query failed');

$query = "FLUSH PRIVILEGES";
mysql_query($query) or die('Error, insert query failed');

echo "New MySQL user added";

###Execute the Expect Script to create mailbox
$output = shell_exec('/var/www/test/smtp.pl smtpdata');
echo "<pre>$output</pre>";

}
else
{

?>
<form method="post">
<table width="400" border="0" cellspacing="1" cellpadding="2">
<tr>
<td width="100">Username</td>
<td><input name="username" type="text" id="username"></td>
</tr>
<tr>
<td width="100">Password</td>
<td><input name="password" type="text" id="password"></td>
</tr>
<tr>
<td width="100">&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td width="100">&nbsp;</td>
<td><input name="add" type="submit" id="add" value="Add New User"></td>
</tr>
</table>
</form>
<?
}
?>

```

After the php script runs it calls the expect perl script which contains the following:

```

###smtp.pl
#!/usr/bin/expect
set inpfile [lindex $argv 0]
set timeo [lindex $argv 1]

# Check for enough args, display usage if we don't have enough.
if 0==$argc {
        send_user "mtaprobe.exp: usage: mtaprobe.exp <input_file> \[timeout\]\n"
        send_user "\nWhere <input_file> is a columnar list of hostnames or IP\n"
        send_user "addresses, and \[timeout\] is an optional timeout value, in\n"
        send_user "seconds.\n"
        exit 1
}

# Set the optional timeout value, in seconds.  Default is 30 seconds.
if {![string compare $timeo ""]} {
        set timeout 30
} else {
        set timeout $timeo
}

# See if we can open the input file
if [catch {open $inpfile} fh] {
        puts "$fh"
        exit 1
}

while {[gets $fh hostie] != -1} {
        send_user "mtaprobe $hostie: beginning...\n"

        spawn telnet $hostie 25

        expect "2?: *" {
                send_user "mtaprobe $hostie: connect failed\n"
                continue
        } "2?? *" {
                send_user "mtaprobe $hostie: connect OK\n"
        } "refused" {
                send_user "mtaprobe $hostie: connect refused\n"
                continue
        } "closed" {
                send_user "mtaprobe $hostie: connect closed\n"
                continue
        } timeout {
                send_user "mtaprobe $hostie: connect to port 25 timeout\n"
                continue
        }

        send_user "mtaprobe $hostie: $expect_out(0,string)\n"

        send "helo mailserver.tld\n"
        expect "250 mail.mailserver.tld" {
                send_user "mtaprobe $hostie: helo OK\n"
        } "5??" {
                send_user "mtaprobe $hostie: helo FAILED\n"
        } timeout {
                send_user "mtaprobe $hostie: helo timeout\n"
        }

        send "mail from: postmaster@mailserver.tld\n"
        expect "2?? " {
                **send "rcpt to: <test@mailserver.tld>\n"**
                expect "2?? " {
                        send_user "mtaprobe $hostie: mail relay ENABLED\n"
                } "5??" {
                        send_user "mtaprobe $hostie: mail relay DENIED\n"
                } timeout {
                        send_user "mtaprobe $hostie: mail relay timeout\n"
                }
        } "5??" {
                send_user "mtaprobe $hostie: mail relay test failed\n"
        } timeout {
                send_user "mtaprobe $hostie: mail relay timeout\n"
        }
        send "data\n"
        expect "354 End data with <CR><LF>.<CR><LF>"
        send "Created User Mailbox\n"
        expect "\n"
        send ".\n"
        expect "2?? "
        send "quit\n"
        send_user "mtaprobe $hostie: completed.\n\n"

}

close $fh

exit

## FINI


```


Basically I want to use the $username variable from create_email.php and pass it to  "send "rcpt to: <test@mailserver.tld>\n" in smtp.pl but I'm at a loss on how this would work.  Anyone have any ideas?

---

### Post by tcpip4lyfe on 2008-06-09
Ended up fixing it myself.  Here's the code:

```
cat create_email_address.php
<html>
<head>
<title>Add New MySQL User</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>
<?

if(isset($_POST['add']))
{
$username = $_POST['username'];
$password = $_POST['password'];

mysql_connect ("localhost", "root", "lolpassword") or die ('Error: ' . mysql_error());
mysql_select_db ("mail");

$query = "INSERT INTO `users` ( `email` , `password` , `quota` )VALUES ('$username', ENCRYPT('$password'), NULL)";
mysql_query($query) or die('Error, insert query failed');

$query = "FLUSH PRIVILEGES";
mysql_query($query) or die('Error, insert query failed');
##Execute mailbox_creation.pl with the argument $username

$output = exec("/var/www/email/mailbox_creation.pl $username");
echo "<pre>$output</pre>";
echo "New MySQL user added";

}
else
{

?>
<body>
<form method="post">
<table width="400" border="0" cellspacing="1" cellpadding="2">
<tr>
<td width="100">Username</td>
<td><input name="username" type="text" id="username"></td>
</tr>
<tr>
<td width="100">Password</td>
<td><input name="password" type="text" id="password"></td>
</tr>
<tr>
<td width="100">&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td width="100">&nbsp;</td>
<td><input name="add" type="submit" id="add" value="Add New User"></td>
</tr>
</table>
</form>

<?
}
?>

```

I found out that syntax is really really important here. 

Then the expect script:
```
cat mailbox_creation.pl

#!/usr/bin/expect
##set the get the username argument from create_email_address.php
set username [lindex $argv 0]
##Run the Expect script
        spawn telnet localhost 25
        #expect "2?: *" {
        send "helo domain.tld\n"
        expect "250 mail1.domain.tld"
        send "mail from: root@localhost\n"
        expect "2?? "
        send "rcpt to:<$username>\n"
        expect "2?? "
        send "data\n"
        expect "354 End data with <CR><LF>.<CR><LF>"
        send "Created User Mailbox\n"
        expect "\n"
        send ".\n"
        expect "2?? "
        send "quit\n"
exit

## FINI

```

I followed "http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04" for setting up postfix and now I have a nice little gui to create the email accounts.  Feel free to use the code if you need.

---

### Post by easyhorpak on 2008-09-01
very nice

---

