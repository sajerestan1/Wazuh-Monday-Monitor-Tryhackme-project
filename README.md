# Wazuh-Monday-Monitor-Tryhackme-project

![Image Description](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*u2blDAFnKarK4oIi.png)


## Endpoint Monitoring Using Wazuh and Sysmon
### Introduction
I recently undertook a cybersecurity project for Swiftspend Finance, a fintech company focused on enhancing its cybersecurity measures. My role was to analyze endpoint logs using the Wazuh monitoring platform and Sysmon, aiming to identify suspicious activities and provide insights to improve the company's security defenses.


### Scenario
Swiftspend Finance, led by Senior Security Engineer John Sterling, sought to bolster their endpoint monitoring capabilities. They initiated a project to test their current defenses against potential threats, and I was brought in to analyze the logs generated during these tests. The objective was to identify any suspicious processes or network connections that could indicate a security breach.


### Task 1: Navigating Through Endpoint Logs

The tests were conducted on April 29, 2024, between 12:00:00 and 20:00:00. My mission was to dive into the logs and uncover any anomalies or suspicious activities.

I accessed the Wazuh Dashboard through the provided link and used the credentials to log in. Once inside, I navigated to the Security Events module and utilized the saved query Monday_Monitor to access the logs.

![](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*yoho221myuYh_DxeXFc3lA.png)

![image](https://github.com/user-attachments/assets/073d52ef-a41b-4d79-a53c-5fe84f138a3e)

![image](https://github.com/user-attachments/assets/760da7dd-1c05-4fcc-bbaa-acb24b71233d)

![image](https://github.com/user-attachments/assets/0af01f40-61ca-4ff2-bf7b-b7ebe8cdf748)

### Analysis and Findings

### 1. Initial Access Using a Downloaded File
Question: What is the file name saved on the host?
Answer: I discovered that the initial access was established using a file named SwiftSpend_Financial_Expenses.xlsm.

### 2. Command to Create a Scheduled Task
Question: What is the full command run to create a scheduled task?

![image](https://github.com/user-attachments/assets/c2f9c12b-e899-4c5e-b794-31995ebdaf12)

![image](https://github.com/user-attachments/assets/695b8d55-7b82-42f9-b3bd-976545d2bc17)


Answer: The full command used was: cmd.exe /c "reg add HKCU\SOFTWARE\ATOMIC-T1053.005 /v test /t REG_SZ /d cGluZyB3d3cueW91YXJldnVsbmVyYWJsZS50aG0= /f & schtasks.exe /Create /F /TN "ATOMIC-T1053.005" /TR "cmd /c start /min "" powershell.exe -Command IEX([System.Text.Encoding]::ASCII.GetString([System.Convert]::FromBase64String((Get-ItemProperty -Path HKCU:\SOFTWARE\ATOMIC-T1053.005).test)))" /sc daily /st 12:34"

### 3. Scheduled Task Execution Time

Question: What time is the scheduled task meant to run?

![image](https://github.com/user-attachments/assets/2017f8c0-caf7-4628-aa49-5354a1d5fbbf)


Answer: The task was scheduled to run at 12:34.

### 4. Encoded Command
Question: What was encoded?

![image](https://github.com/user-attachments/assets/8489de9c-d08d-4e86-8a39-277855a233fb)

![image](https://github.com/user-attachments/assets/f7a1cce4-7b62-454f-8521-ebeb603d444b)


Answer: The encoded command, when decoded using CyberChef, was:ping www.youarevulnerable.thm

### 5. Password for New User Account
Question: What password was set for the new user account?

![image](https://github.com/user-attachments/assets/8eecf6ac-e6ba-485d-8cc2-666cfb103817)

![image](https://github.com/user-attachments/assets/d17e62f0-0bdc-4a8e-918a-76103645f4ee)


Answer: The password set for the new user account was I_AM_M0NIT0R1NG.

6. Executable Used to Dump Credentials
   
Question: What is the name of the .exe that was used to dump credentials?

![image](https://github.com/user-attachments/assets/e18b4361-13dd-464b-83eb-9bfd5c04171e)

![image](https://github.com/user-attachments/assets/5998b268-6d64-431a-8021-049bd734bc95)



Answer: The executable used to dump credentials was memotech.exe.

### 7. Exfiltrated Data Flag
Question: Data was exfiltrated from the host. What was the flag that was part of the data?

![image](https://github.com/user-attachments/assets/10f8a418-4c4f-4c1d-9e53-5105a23a84d6)
![image](https://github.com/user-attachments/assets/54d10a7a-c0bd-4951-9f0a-18336ebd934f)


Answer: The flag that was part of the exfiltrated data was: THM{M0N1T0R_1$_1N_3FF3CT}

### Conclusion
Through this project, I successfully identified and analyzed several suspicious activities within the endpoint logs, demonstrating the effectiveness of Wazuh and Sysmon in monitoring and securing endpoints. The insights gained from this analysis will help Swiftspend Finance fine-tune their cybersecurity defenses and better protect their digital assets against potential threats
