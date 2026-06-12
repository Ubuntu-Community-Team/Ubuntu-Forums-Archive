---
title: "Php5 + Mssql"
date: 2007-02-26
forum: General Help
---

### Post by AllSystemGo on 2007-02-26
Ok I'm trying to connect to a MSSQL database that's on an other server. I installed all packages about the ODBC drivers and the FreeTDS with Synaptic. But it still doesn't want to connect to the DB what did I do wrong??

Here's my PHP coding

[PHP]
<html>
  <body>
    <?php
      require_once 'mssql.php';

      echo 'test1';

       $db_conn = mssql_connect("10.128.0.10", "user", "password")
          or die( "<strong>ERROR: Connection to 10.128.0.10 failed</strong>" );
        mssql_select_db( "CCM0304", $db_connect )
          or die( "<strong>ERROR: Selecting database failed</strong>" );
        $query_result = mssql_query( "SELECT * FROM Pilot" )
          or die( "<strong>ERROR: Query failed</strong>" );

        mssql_close( $db_conn );

    ?>
  </body>
</html>
[/PHP]

I get this error
Fatal error: Call to undefined function mssql_connect() in /var/www/apache2-default/intranet/test.php on line 56

---

### Post by nereid on 2007-02-26
Um, do you mean MySQL?

---

### Post by AllSystemGo on 2007-02-26
Nope I need to access a SQL Server 2000 DB

---

### Post by nikhilk on 2007-02-26
Is the php code you have posted the /var/www/apache2-default/intranet/test.php file? The error occurs at line number 56 in file /var/www/apache2-default/intranet/test.php. Your code doesnt have that many lines, kindly elaborate.

---

### Post by AllSystemGo on 2007-02-26
yeah sorry for that. I removed some of the non-necessary code.

Here is the code and the error

[PHP]
<html>
  <body>
    <?php
	$db_conn = mssql_connect("10.128.0.10", "user", "password")
          or die( "<strong>ERROR: Connection to 10.128.0.10 failed</strong>" );
        mssql_select_db( "CCM0304", $db_connect )
          or die( "<strong>ERROR: Selecting database failed</strong>" );
        $query_result = mssql_query( "SELECT * FROM Pilot" )
          or die( "<strong>ERROR: Query failed</strong>" );

        mssql_close( $db_conn );

    ?>
  </body>
</html>
[/PHP]

Fatal error: Call to undefined function mssql_connect() in /var/www/apache2-default/intranet/test.php on line 4

Sorry for that!!

---

### Post by nereid on 2007-02-26
Maybe the Ubuntu version of PHP isn't compiled with mssql support. What does phpinfo() say?

---

### Post by der_joachim on 2007-02-26
You need to use the odbc functions instead of the mssql driver. So, instead of using mssql_connect you'll have to use odbc_connect.

See [here]("http://www.php.net/manual/en/ref.uodbc.php") for additionbal information.

---

