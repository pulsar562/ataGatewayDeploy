# Advanced Threat Analytics (ATA) Gateway Deployment
This script will deploy the ATA Gateway to domain controllers or standalone ATA Gateway servers.

ATA Gateway servers must be enabled for PowerShell remoting (see Enable-PSRemoting)
The script will prompt for credentials.  These credentials require read, write and execute privileges on the gateway servers (usually a DADM).

The script's $userName and $userPwd are the local account created on the ATA Server that is a member of Microsoft Advanced Threat Analytics Administrator group.   
Ensure that this low privileged account is used and consider changing the password afterward.

The script will launch a job for each server:

copy Microsoft ATA Gateway Setup.zip file 

extract Microsoft ATA Gateway Setup.zip file 

run the Microsoft ATA Gateway Setup.exe file with /q (quiet) parameter. Prevents restart (/norestart).  If restart is desired remove the /norestart parameter in the command line.

###Assumes: 
Gateways meet minimum software and hardware requirements.  
Credential provided has adequate permissions to initiate a PSSession to host.  
Script is run as an administrator with permissions to create a folder and copy install media to host.  
User name and password provided are a valid user in the local ATA Center Microsoft Advanced Threat Analytics Administrators group.  
The correct ATA Gateway zip file is referenced.  
Input and output files have valid locations.  
Active Directory module has been installed on client machine.

###Parameters:
    Mandatory:
    $zipMediaName - full path and name to the zip file, e.g. "c:\temp\microsoft ata gateway setup.zip"
    $userName - user name with privileges to install gateway
    $userPwd - password for user
    $serverFileName file name that has the list of domain controllers/standalone servers to install. 
   
    Defaults:
    
    Parameter $completedFile defaults to c:\temp\ATADeployCompleted.csv
    Parameter $destinationRootPath defaults to c$\temp\ - appends to UNC filepath
