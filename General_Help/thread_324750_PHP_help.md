---
title: "PHP help"
date: 2006-12-24
forum: General Help
---

### Post by rado_london on 2006-12-24
Hey people
I run a webserver and today I did a registration form called query.html. Once the user clicks submit it displays the result in register.php and the user can see it. At the moment I do it so it is visible but I plan to hide it from the user:)

Now when I click submit I get some error:
```
Parse error: syntax error, unexpected T_CONSTANT_ENCAPSED_STRING, expecting ',' or ';' in /opt/lampp/htdocs/site/register.php on line 8
```

Here is the query.html:
```
rado@ubuntu:/media/HACKINTOSH/www.maxstorage.tk$ cat query.html 
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>



  
  
  
  <title>Register with MAXstorage</title>
</head>


<body style="color: red; background-color: rgb(204, 204, 204); background-image: url(images/tile.png);" basefont="5" font="" color="yellow" alink="#000099" link="#000099" vlink="#990099">




<h1 style="color: rgb(0, 0, 0);" align="center">MAXstorage
registration form</h1>




<br>




<form method="post" action="register.php" onsubmit="" name="email">
  
  
  
  <p><br>




  </p>




  
  
  
  <table style="width: 836px; height: 245px;" border="0">




    <tbody>




      <tr>




        <td style="width: 23%; height: 23px; color: rgb(51, 51, 51);">
Your Name</td>




        <td style="width: 77%; height: 23px;"><input name="name" size="30" type="text"></td>




      </tr>




      <tr>




        <td style="width: 23%; height: 23px; color: rgb(51, 51, 51);">Your
Email
address</td>




        <td height="23" width="77%"><input name="email" size="30" type="text"></td>




      </tr>




      <tr>




        <td style="height: 23px; color: rgb(51, 51, 51); width: 30%;">MAXstorage
username</td>




        <td height="23" width="77%"><input name="username" size="30" type="text"></td>




      </tr>




      <tr>




        <td style="color: rgb(51, 51, 51); vertical-align: top; width: 40px;">MAXstorage
password</td>




        <td style="vertical-align: top; width: 40px;"><input name="password" size="30"></td>




      </tr>




      <tr>




        <td style="width: 23%; height: 23px; vertical-align: top; color: rgb(51, 51, 51);">
Enquiry Details</td>




        <td height="99" width="77%"> <textarea rows="4" name="enquiry" cols="35"> </textarea>
        
        
        
        <p><br>




        </p>




        </td>




      </tr>




      <tr>




      </tr>



    
    
    
    </tbody>
  
  
  
  </table>




  
  
  
  <p align="center"> <input name="Request" value="Submit This Form" type="submit">
  <input name="Clear" value="Clear Form and Start Over" type="reset"></p>




</form>




</body>
</html>

```

Here is the ioutput for register.php:
[PHP]<html><body>
<?php
$name = $_POST['name'];
$email = $_POST['email'];
$username = $_POST['usename'];
$password = $_POST['password'];

echo "Your name is: ".$name"<br />";
echo "Your email address is: ".$email"<br>";
echo "Your username is: ".$username" <br>";
echo "Your password is: ".$password" <br>";

?>
</body></html>
[/PHP]

WHat is wrong with the whole thing?

---

### Post by peterx14 on 2006-12-24
I think you either need to use an extra string concatenation operator (.) or just go with the double-quotes you're using, e.g. either:
```
echo "Your name is: " . $name . "<br />";
echo "Your email address is: " . $email . "<br>";
echo "Your username is: " . $username . " <br>";
echo "Your password is: " . $password . " <br>";
```

or:
```
echo "Your name is: $name<br />";
echo "Your email address is: $email<br>";
echo "Your username is: $username<br>";
echo "Your password is: $password<br>";
```

HTH!

---

### Post by rado_london on 2006-12-24
> **peterx14 said:**
> I think you either need to use an extra string concatenation operator (.) or just go with the double-quotes you're using, e.g. either:
```
echo "Your name is: " . $name . "<br />";
echo "Your email address is: " . $email . "<br>";
echo "Your username is: " . $username . " <br>";
echo "Your password is: " . $password . " <br>";
```

or:
```
echo "Your name is: $name<br />";
echo "Your email address is: $email<br>";
echo "Your username is: $username<br>";
echo "Your password is: $password<br>";
```

HTH!

Thank you very much now it works. Now I want to display a page saying thanks and we will process your request ASAP. On the other hand I want this info  to be sent to a email address so I can process it. How can I do that?

---

### Post by peterx14 on 2006-12-24
You know these are more PHP questions than Ubuntu questions don't you? Anyway, since its Christmas....

I just dug this email example out from somewhere -- I'm not sure who originally wrote it (it might even be an example from a book):

```
<?php
// multiple recipients
$to  = 'aidan@example.com' . ', '; // note the comma
$to .= 'wez@example.com';

// subject
$subject = 'Birthday Reminders for August';

// message
$message = '
Birthday Reminders for August
-----------------------------

Here are the birthdays upcoming in August!

Person         Day   Month     Year
Joe            3rd   August    1970
Sally          17th  August    1973
';

// Additional headers
$headers .= 'To: Mary <mary@example.com>, Kelly <kelly@example.com>' . "\r\n";
$headers .= 'From: Birthday Reminder <birthday@example.com>' . "\r\n";
$headers .= 'Cc: birthdayarchive@example.com' . "\r\n";
$headers .= 'Bcc: birthdaycheck@example.com' . "\r\n";

// Mail it
mail($to, $subject, $message, $headers);
?>

```

The above example creates a plain text formatted email. This next example creates a HTML formatted email:

```
<?php
// multiple recipients
$to  = 'aidan@example.com' . ', '; // note the comma
$to .= 'wez@example.com';

// subject
$subject = 'Birthday Reminders for August';

// message
$message = '
<html>
<head>
	<title>Birthday Reminders for August</title>
</head>
<body>
	<p>Here are the birthdays upcoming in August!</p>
	<table>
		<tr>
			<th>Person</th><th>Day</th><th>Month</th><th>Year</th>
		</tr>
		<tr>
			<td>Joe</td><td>3rd</td><td>August</td><td>1970</td>
		</tr>
		<tr>
			<td>Sally</td><td>17th</td><td>August</td><td>1973</td>
		</tr>
	</table>
</body>
</html>
';

// To send HTML mail, the Content-type header must be set
$headers  = 'MIME-Version: 1.0' . "\r\n";
$headers .= 'Content-type: text/html; charset=iso-8859-1' . "\r\n";

// Additional headers
$headers .= 'To: Mary <mary@example.com>, Kelly <kelly@example.com>' . "\r\n";
$headers .= 'From: Birthday Reminder <birthday@example.com>' . "\r\n";
$headers .= 'Cc: birthdayarchive@example.com' . "\r\n";
$headers .= 'Bcc: birthdaycheck@example.com' . "\r\n";

// Mail it
mail($to, $subject, $message, $headers);
?>
```

Obviously to make this work, you'll need to insert your variables similarly to what you did before.

Any other questions.... well, I might not reply what with Christmas an' all! But, google is your friend. Also, this [PHP Tutorial](http://www.thesitewizard.com/archive/feedbackphp.shtml) might be good.

All the best,

Peter.

---

### Post by rado_london on 2006-12-24
I will post one more time. I use the Ubuntu Forums as they are the best place for help IMO.
So I edited the script. Now it looks like this:
[PHP]<?php
// multiple recipients
$to  = 'register.maxstorage@googlemail.com' . ', '; // note the comma


// subject
$subject = 'MAXstorage Registration Request';

// message
$name = $_POST['name'];
$email = $_POST['email'];
$username = $_POST['usename'];
$password = $_POST['password'];
$message = '
echo "Your name is: $name<br />";
echo "Your email address is: $email<br>";
echo "Your username is: $username<br>";
echo "Your password is: $password<br>";
';
//Additional Headers
$headers .= 'To: Me <register.maxstorage@googlemail.com>'. "\r\n";
$headers .= 'From: register MAXstorage <petsov@googlemail.com>'. "\r\n";
// Mail it
mail($to, $subject, $message, $headers);
?>[/PHP]

When I click submit it goes to a blank page and does nothing. I check my inbox I dont have any email.
Anyone knows what is wrong with my script?

---

### Post by rado_london on 2006-12-25
Christmas BUMP

---

### Post by hanzomon4 on 2006-12-25
deleted

---

### Post by rado_london on 2006-12-25
> **hanzomon4 said:**
> deleted

????

---

