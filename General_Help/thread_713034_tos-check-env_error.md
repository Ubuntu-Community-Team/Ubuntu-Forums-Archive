---
title: "tos-check-env error"
date: 2008-03-02
forum: General Help
---

### Post by Jacques Kleynhans on 2008-03-02
I recently installed tinyos wireless motes and now by setting the env variables i get an compile error.

tos2x() {
        export TOSROOT=/opt/tinyos-2.x
	export TOSDIR=$TOSROOT/tos
	export CLASSPATH=$TOSROOT/support/sdk/java/tinyos.jar:.
	export MAKERULES=$TOSROOT/support/make/Makerules
	export PATH=$PATH:/opt/msp430/bin	
        }

is there anything wrong here.

i get an error tos-check-env completed with errors:

--> WARNING: CLASSPATH environment variable doesn't exist.
Your classpath should contain  and a pointer 
to the cwd (a dot)

---

### Post by Jacques Kleynhans on 2008-03-02
Im getting compile errors with the env check command

--> WARNING: CLASSPATH environment variable doesn't exist.
Your classpath should contain  and a pointer 
to the cwd (a dot)

i have a . there

tos2x() {
        export TOSROOT=/opt/tinyos-2.x
	export TOSDIR=$TOSROOT/tos
	export CLASSPATH=$TOSROOT/support/sdk/java/tinyos.jar:.
	export MAKERULES=$TOSROOT/support/make/Makerules
	export PATH=$PATH:/opt/msp430/bin	
        }

---

