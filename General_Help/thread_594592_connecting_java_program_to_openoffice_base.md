---
title: "connecting java program to openoffice base"
date: 2007-10-28
forum: General Help
---

### Post by jittopjose on 2007-10-28
i am using feisty,
now am doing a small java program that connect to openoffice base.
the program i wrote is given below. while running i always got error as  "java.sql.SQLException: Table not found in statement [select * from test]"
it didnt make any problem at the time of connection establishment. but at the time of executeQuery(), it produce exception
plz help me if anybody know anything about this problem




the code is ..

import java.sql.*;


public class TestDb {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("hai");
		
		
		try {
			Class.forName("org.hsqldb.jdbcDriver");
		}
		catch(ClassNotFoundException e) {
			System.out.println(e);
		}
		
		try {
			Connection con=null;
			try{
			con=DriverManager.getConnection("jdbc:hsqldb:jittodb");
			}catch(Exception e){
				System.out.println(e.getMessage());
			}
			System.out.println(con.toString());
			Statement st=con.createStatement();
			System.out.println(st.toString());
			String s="create table test (name varchar(20))";
			//String s="insert into login values('jitto')";
			ResultSet rs=st.executeQuery("select * from test");
			//st.executeQuery(s);
			
		st.close();
		con.close();

		}
		catch(SQLException e){
			System.out.println(e);
		}
		

	}

}





error found:--

"java.sql.SQLException: Table not found in statement [select * from test]"



thanks
jittos....

---

### Post by jenhsun on 2007-10-28
Here you go
[http://forum.java.sun.com/thread.jspa?threadID=677340&tstart=165](http://forum.java.sun.com/thread.jspa?threadID=677340&tstart=165)

I wonder is that your post??

---

### Post by jittopjose on 2007-10-29
thank u for ur replay my friend.
i saw that post earlier. but nobody answered to that question properly. i thought this might be a problem when working with linux. thats why i posted it here. still i am unable to connect ..  anybody know any idea to resolve this, plz reply
thanks
jittos....

---

### Post by jenhsun on 2007-10-29
[http://hsqldb.org/web/hsqlDocsFrame.html](http://hsqldb.org/web/hsqlDocsFrame.html)

---

### Post by jittopjose on 2007-10-29
thank u my friend.
i think that link would be useful. let my try. and shall of course post the result.
thank u
jittos....

---

### Post by jenhsun on 2007-10-29
> **jittopjose said:**
> thank u my friend.
i think that link would be useful. let my try. and shall of course post the result.
thank u
jittos....

No problem. I know what you're trying to do.
Go to this site [http://www.oooforum.org/](http://www.oooforum.org/)
and do a serach: HSQLDB
I think you will get what you want.

---

### Post by jittopjose on 2007-10-29
thank u .....

---

