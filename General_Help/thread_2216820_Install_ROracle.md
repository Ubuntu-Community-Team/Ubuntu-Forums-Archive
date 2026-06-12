---
title: "Install ROracle"
date: 2014-04-14
forum: General Help
---

### Post by bkbilly2 on 2014-04-14
I want to install **ROracle** in my Ubuntu machine 64bit and I am having some problems...
what I did is:
download the oracle instant client from here: [http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html](http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html)
I downloaded the **basic** and **devel** rpm files.

then I did the following:
```

sudo apt-get install alien libaio1
sudo alien -i oracle-instantclient12.1-basic*.rpm
sudo alien -i oracle-instantclient12.1-devel*.rpm

export LD_LIBRARY_PATH=/usr/lib/oracle/12.1/client64/lib
export ORACLE_HOME=/usr/lib/oracle/12.1/client64
sudo mkdir $ORACLE_HOME/rdbms
sudo mkdir $ORACLE_HOME/rdbms/public
sudo cp /usr/include/oracle/12.1/client64/* $ORACLE_HOME/rdbms/public

R CMD INSTALL ~/Downloads/ROracle_1.1-11.tar.gz 

```

it starts compiling, but there is an error that says "**/usr/bin/ld: cannot find -lclntsh**"
I goggled the problem and they say that it is a problem with the symbolic links but I can see that they are fine!

Can you help me?

---

### Post by coffeecat on 2014-04-14
Not a Tutorial.

*Thread moved to **General Help**.*

---

### Post by nemo3 on 2014-07-30
Basically, you must set with-oci-inc and with-oci-lib, like this

First, install.packages('DBI')
return to terminal and do:
- go to home directory
# cd
- get the .tar.gz 
# wget [http://cran.r-project.org/src/contrib/ROracle_1.1-11.tar.gz](http://cran.r-project.org/src/contrib/ROracle_1.1-11.tar.gz)
- Install  ROracle with some args
R CMD INSTALL --configure-args='--with-oci-inc=/usr/lib/oracle/11.2/client64/include --with-oci-lib=/usr/lib/oracle/11.2/client64/lib' ROracle_1.1-11.tar.gz

---

### Post by bkbilly2 on 2014-07-31
I totally forgot about my post :p
Thanks for your reply though!
I will try it some time.

I managed to connect to the oracle DB with the RJDBC.
In case anyone wants this is the code I used:
```

ConnectDB = function(){
  library(rJava)
  library(RJDBC)
  .jinit()
  drv <- JDBC(driverClass="oracle.jdbc.OracleDriver", classPath="/path/to/ojdbc6.jar")
  con <- dbConnect(drv, "jdbc:oracle:thin:@//IP:port/sid", "UserName", "Password")
  return(con)
}
con <- ConnectDB()

```

---

