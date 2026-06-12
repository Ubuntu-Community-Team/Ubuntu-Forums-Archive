---
title: "Paramiko ssh could not locate executable"
date: 2014-10-21
forum: General Help
---

### Post by andres18 on 2014-10-21
I have an Amazon Web Services computer that runs a python script (Pyomo followed by calling Gurobi). When I run the script via SSH through Putty I have no issue when I run it as the user 'ubuntu'. However when I run it from sudo I get the error below.  

I am trying to run the script through the Python Paramiko SSH module, however when I run it like that (from 'ubuntu') it gives me the same results as when I run it from sudo through Putty. Does anyone know how to fix this?


Paramiko Code Excerpt:
 ssh_stdin, ssh_stdout, ssh_stderr = ssh.exec_command("python Main2_AWS_side.py",bufsize=-1)
 print "AWS side started"
 print ssh_stdout.read()
 print ssh_stdout.read() #Lots of code runs, if I only use one it doesnt display it all.
 exit_status = ssh_stdout.channel.recv_exit_status()


ERROR:
"Model created, starting to solve 32.554692
WARNING: "[base]/dist-packages/coopr/opt/base/solvers.py", 209, __solver_call__
    DEPRECATION WARNING: beginning in Coopr 4.0, plugins (including
    solvers and DataPortal clients) will not be automatically registered. To
    automatically register all plugins bundled with core Coopr, user scripts
    should include the line, "import coopr.environ".
WARNING: "[base]/dist-packages/coopr/solvers/plugins/solvers/GUROBI.py", 200, executable
    Could not locate the 'gurobi' executable, which is required for solver gurobi"

---

