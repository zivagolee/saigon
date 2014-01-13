saigon
======

Saigon - Zynga's Central Nagios Configuration Service

            Managing a large infrastructure can be challenging -- to say the least -- and monitoring that infrastructure can be even tougher. At Zynga we have approached this problem by providing our teams with a central micro-system which allows them leverage Nagios and to use standards without having to even know them. Saigon allows core teams familiar with Nagios to push service checks, command definitions, and various other bits of Nagios and NRPE configurations to our Studios for consumption and adoption. Saigon works by using an inheritance model inside of the application, much like Nagios, which allows for these subject matter experts to expose information from one common or core deployment into another, which is in turn leveraged by the Studio.
 
            Saigon's inner workings tie metadata it stores about Nagios configuration files and one or more host API interfaces together, such as Ec2, Rightscale, or even your own custom CMDB (configuration management database). The modularization of this action in our code base has allowed us to interface with various host stores and still produce trusted Nagios configurations without risking our standards. We are able to verify and test our builds on demand, investigate our configurations by viewing them in the user interface, or even diff between revisions to find out what changes were made. All of these abilities are provided in our user interface thus allowing us to create and manage well over a million checks crossing 50+ different Saigon managed Nagios deployments.
 
            Some of the key benefits we feel Saigon has over original approaches to Nagios configuration systems is that Saigon actually interfaces with various Host APIs and uses those live real time calls to populate the Nagios configuration files when they are built. Saigon has an internal versioning mechanism it uses to make sure only the currently blessed revision is being detected by callback consumers, thus maintaining your environment while you make changes to your Nagios or NRPE configuration files. Saigon's design allows it to manage Nagios object files, as well as the core configuration files; such as cgi.cfg, resource.cfg, nagios.cfg, or even Mod-Gearman configuration files. Saigon also allows us to fully manage the NRPE stack, configuration files and plugins. The consumers will ensure these files and plugins exist on the system, while also ensuring the contents of these files matches exactly what they are being told to create or modify.
 
            This full stack management allows for Studios to be able to manage and operate their own Nagios instance, while a core infrastructure group can manage and operate their own Nagios instance, but be configured to access a different NRPE port / daemon. This does require us to run a secondary NRPE daemon, but it also helps to differentiate between core infrastructure checks and studio checks. Now yes, we could implement supplemental NRPE configuration files (Saigon does support this), however our needs would not have been met by this approach due to initial limitations we had done to ourselves, in our own environment.
 
            Saigon is still very much under active development, and maturing every day. We have recently added a Form Based / JSON based API integration point, the hopes here are to be able to create a better UI that can help move it into the 21st century ;), while also providing a programmatic way for people to integrate with Saigon. Modularization of the back end data store, so it can function more like the host API integration point, thus allowing for people to integrate with their favorite datastore of choice, and not being subjected to run Redis (although it does function quite nicely for this program). And of course we are always looking for ways to make the product better and improve the state of sysadmin Nagios management around the world, so feel free to reach out to us if you have any suggestions, bugs, or ideas we could put into future versions.
