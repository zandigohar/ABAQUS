# ABAQUS-CAE (SIMULIA) Instalation in Ubuntu - SolidSquad SSQ Team

Step 1: PRE-REQS

Install ksh shell interpreter

```
        sudo apt-get update -y
        sudo apt-get install -y ksh
```
Install lsb-release
```
        sudo apt-get update -y
        sudo apt-get install -y lsb-release
```
Step 2: SERVER

Install (or modify) the installation of ABAQUS License Server
  2.1 Login as root
  ```
        sudo -s
  ```
  2.2 Unpack simulia.tar.gz to a destination, say /usr/. This is the license files folder that needs to be started.
  	How to open or Untar a "tar.gz" file in Linux or Unix:
	  The following tutorial assumes the name of your file is yourfile.tar.gz Replace with your actual filename.
	  From the terminal, change to the directory where yourfile.tar.gz has been downloaded.
	  Type ```tar -zxvf yourfile.tar.gz``` to extract the file to the current directory.
	  You can specify a different directory to extract to using ```-C``` parameter and a path to the directory as follows:
	  Example: ```tar -C /myfolder -zxvf yourfile.tar.gz```
  
  2.3 Start ABAQUS license server
  
          /usr/simulia/license/lmgrd -c /usr/simulia/license/ABAQUS.lic	

    You can either kill the process to restart by
    
    	killall -9 ABAQUSLM
    
    or go to htop and search the process and kill it manually.
    This initiation process may need some libraries to be installed. Use sudo apt-get <required library> to install it.       
    Using Google search helps to find the exact terminologies.
  
  There was no documnetations included in the downloaded file, so the documentations installation was igonred.
  
  Step 3: ABAQUS INSTALLATION
  
  While staying as root in terminal, it's time to install DS SIMULIA ABAQUS 2016.
  3.1 Mount the ISO image. You can either do it manually or via terminal. The mounted file will be available in mount         
      folder.
  
  3.2 Start installation process sequentially:

       3.2.1 ABAQUS SOLVERS using command-line:       
              cd <mounted CD folder>
	            export DSYAuthOS_`lsb_release -si`=1 && export DSY_Force_OS=linux_a64 && ksh ./StartGUI.sh     
	            Installation Directory: /opt/DassaultSystemes/SimulationServices/V6R2016X
	             *Note: If error occured (not found error): Make the directory, each level at a time by 
                    mkdir <directoryName>
              **Note: If the installer asked to remove a duplicated folder use this:
                    

       3.2.2 ABAQUS CAE using command-line from step 2.4

            Installation Directory: /opt/DassaultSystemes/SIMULIA/CAE/2016/
	          Path To ABAQUS Solvers: /opt/DassaultSystemes/SimulationServices/V6R2016X
	          Path to ABAQUS Commands: /var/DassaultSystemes/SIMULIA/ (by default)
	          Licensing: SIMULIA FlexNet with "27011@localhost" as License Server 1
	          Working Directory: /var/tmp (default)
            *Note: The installation may get stuck for a while, especifically when the file removal process begins, 
                   you may cancel isntallation and still get your installation completed.
           
    
  Step 4: SOFTWARE RUN
    
      To run, use the following command:
	      /var/DassaultSystemes/SIMULIA/Commands/abq2016 cae (you may also add sudo)
      However, if error occured you need to install required libraries. 
      Probably: apt install libstdc++5 and apt install libjpeg62 
      Maybe: apt install gcc-5 and apt install g++-5
      If the error still occured use the following      
      command:
          sudo /var/DassaultSystemes/SIMULIA/Commands/abq2016 cae -mesa
      This may make graphics low quality, transparent or disatisfactory.
      
 Appendix
 
  A.1 Getting Graphics Card Info
  
      ```sudo lshw -c video```
    
This is the end of manual.
