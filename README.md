![vm cycle (1)](https://github.com/user-attachments/assets/76f874f5-3ebc-470a-abc3-c900cd2a10b7)
# Vulnerabilty-Management-with-Tenable
A project to simulate the inception and implementation of a vulnerability management policy. In this case we assume:

_**Inception State:**_ the organization has no existing policy or vulnerability management practices in place.

_**Completion State:**_ a formal policy is enacted, stakeholder buy-in is secured, and a full cycle of organization-wide vulnerability remediation is successfully completed.

---

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/cfc5dbcf-3fcb-4a71-9c13-2a49f8bab3e6">

# Technology Utilized
- Tenable (enterprise vulnerability management platform)
- Azure Virtual Machines (Nessus scan engine + scan targets)
- PowerShell & BASH (remediation scripts)

---



# Table of Contents

- [Vulnerability Management Policy Draft Creation](#vulnerability-management-policy-draft-creation)
- [Mock Meeting: Policy Buy-In (Stakeholders)](#step-2-mock-meeting-policy-buy-in-stakeholders)
- [Policy Finalization and Senior Leadership Sign-Off](#step-3-policy-finalization-and-senior-leadership-sign-off)
- [Mock Meeting: Initial Scan Permission (Server Team)](#step-4-mock-meeting-initial-scan-permission-server-team)
- [Initial Scan of Server Team Assets](#step-5-initial-scan-of-server-team-assets)
- [Vulnerability Assessment and Prioritization](#step-6-vulnerability-assessment-and-prioritization)
- [Distributing Remediations to Remediation Teams](#step-7-distributing-remediations-to-remediation-teams)
- [Mock Meeting: Post-Initial Discovery Scan (Server Team)](#step-8-mock-meeting-post-initial-discovery-scan-server-team)
- [Mock CAB Meeting: Implementing Remediations](#step-9-mock-cab-meeting-implementing-remediations)
- [Remediation Round 1: Outdated Wireshark Removal](#remediation-round-1-outdated-wireshark-removal)
- [Remediation Round 2: Insecure Protocols & Ciphers](#remediation-round-2-insecure-protocols--ciphers)
- [Remediation Round 3: Guest Account Group Membership](#remediation-round-3-guest-account-group-membership)
- [Remediation Round 4: Windows OS Updates](#remediation-round-4-windows-os-updates)
- [First Cycle Remediation Effort Summary](#first-cycle-remediation-effort-summary)

---

### Step 1) Vulnerability Management Policy Draft Creation

This phase focuses on drafting a Vulnerability Management Policy as a starting point for stakeholder engagement. The initial draft outlines scope, responsibilities, and remediation timelines, and may be adjusted based on feedback from relevant departments to ensure practical implementation before final approval by upper management.  
[Draft Policy](https://docs.google.com/document/d/1CLSWm1_9JL1oUqgyNNwtPXW6FzXJ7ddVnSAUQTyqC8I/edit?usp=drive_link)

---

### Step 2) Mock Meeting: Policy Buy-In (Stakeholders)

In this phase, a meeting with the server team introduces the draft Vulnerability Management Policy and assesses their capability to meet remediation timelines. Feedback leads to adjustments, like extending the critical remediation window from 48 hours to one week, ensuring collaborative implementation.

<details>
<summary>Click to expand meeting text</summary>
    
![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) **Zack (Vulnerability Analyst):** Hey, good morning, Jimmy! How's everything been recently? I know everyone's been busy these last few weeks.

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) **Jimmy (Server Team):** Good morning, Zack! Yeah, it's been a bit hectic, but we're hanging in there. Thanks for asking. I had a chance to read through the policy draft, and overall it makes sense. However, with our current staffing, we can't meet the aggressive remediation timelines, especially the 48-hour window for critical vulnerabilities.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) **Zack (Vulnerability Analyst):** I totally understand. It is a bit aggressive, especially to start. Perhaps we can extend the critical timeline to one week? It might be a good compromise for now, and we can reserve the 48-hour window for truly severe zero-day vulnerabilities.

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) **Jimmy (Server Team):** That sounds reasonable. We appreciate the flexibility. Can we have a bit of leeway in the beginning as we work through getting used to the remediation and patching process, just for the first few months?

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) **Zack (Vulnerability Analyst):** Absolutely. After the policy is finalized, we'll officially start the program, but we're planning to give all the departments about six months to adjust to the new process. Does that sound fair?

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) **Jimmy (Server Team):** Thanks, Zack. We'll do our best. I appreciate you including us in the decision-making process; it really helps us feel like we're part of the solution.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) **Zack (Vulnerability Analyst):** Of course! We're all in this together. Thanks for working with us.

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) **Jimmy (Server Team):** No problem! Thanks for the short meeting.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) **Zack (Vulnerability Analyst):** Yeah, those are my favorite types. Bye for now!

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) **Jimmy (Server Team):** See you later!


</details>

---

### Step 3) Policy Finalization and Senior Leadership Sign-Off

After gathering feedback from the server team, the policy is revised, addressing aggressive remediation timelines. With final approval from upper management, the policy now guides the program, ensuring compliance and reference for pushback resolution.  
[Finalized Policy](https://docs.google.com/document/d/1rvueLX_71pOR8ldN9zVW9r_zLzDQxVsnSUtNar8ftdg/edit?usp=drive_link)

![approved](https://github.com/user-attachments/assets/1e8ea0ff-c986-45b0-b2a6-a546ed92dc5f)

---

### Step 4) Mock Meeting: Initial Scan Permission (Server Team)

The team collaborates with the server team to initiate scheduled credential scans. A compromise is reached to scan a single server first, monitoring resource impact, and using just-in-time Active Directory credentials for secure, controlled access.  

<details>
<summary>Click to expand meeting text</summary>
    
**![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst):** Good morning!

**![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team):** Good morning, Zack! I heard you’re ready to conduct some scans.

**![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst):** Yep! Now that our vulnerability management policy is in place, I wanted to get started on conducting some scheduled credential scans of your environment.

**![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team):** Sounds good to me! What’s involved? How can we help?

**![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst):** We’re planning to schedule some weekly scans of the server infrastructure. We estimate it’ll take about 4 to 6 hours to scan all 200 assets. We’ll need you to provide us with some administrative credentials, which will allow the scan engine to remotely log into the targets to better assess them.

**![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team):** Whoa, whoa! Hold on there. What does scanning actually entail? I’m a bit worried about resource utilization. Also, you want admin credentials to all 200 machines? That doesn’t sound safe.

**![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst):** Those are valid concerns. The scan engine basically sends different traffic to the servers that will check for the existence of certain vulnerabilities. This includes looking into the registry and checking if certain out-of-date software is installed or if there are any insecure protocols or suites. That’s why credentials are required.

**![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team):** I see. Well, as long as it doesn’t bring the servers offline, I guess we should be okay.

**![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst):** Absolutely! Let’s just scan a single server for now and keep an eye on the resource utilization.

**![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team):** Not a bad idea. Great! Also, for the credentials, can you set up something in Active Directory for us? Like some Active Directory credentials? You can just leave them disabled until we’re ready to do the scan, and then enable them during the scan. After it’s finished, we can deprovision or at least disable that account—kind of like a just-in-time access situation.

**![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst):** That sounds good! I’ll ask Susan to get started on the automation for the account provisioning.

**![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team):** Awesome! Okay, talk soon.

</details>

---

### Step 5) Initial Scan of Server Team Assets

In this phase, an insecure Windows Server is provisioned to simulate the server team's environment. After creating vulnerabilities, an authenticated scan is performed, and the results are exported for future remediation steps.  

<img width="635" alt="Scan 1" src="https://github.com/user-attachments/assets/c0af6fd3-5aaf-4608-890d-5e2bf11af19c" style="border: 2px solid black;"/>

[Scan 1 - Initial Scan](https://drive.google.com/file/d/1c_OdRGN8cJqEBANynG6Y1GgVBLEd48R_/view?usp=sharing)




---

### Step 6) Vulnerability Assessment and Prioritization

We assessed vulnerabilities and established a remediation prioritization strategy based on ease of remediation and impact. The following priorities were set:

1. Third Party Software Removal (Wireshark)
2. Windows OS Secure Configuration (Protocols & Ciphers)
3. Windows OS Secure Configuration (Guest Account Group Membership)
4. Windows OS Updates

---

### Step 7) Distributing Remediations to Remediation Teams

The server team received remediation scripts and scan reports to address key vulnerabilities. This streamlined their efforts and prepared them for a follow-up review.  

<img width="635" alt="image" src="https://github.com/user-attachments/assets/bbf9478f-e1d1-4898-846e-b510ec8c6f72">

---

### Step 8) Mock Meeting: Post-Initial Discovery Scan (Server Team)

The server team reviewed vulnerability scan results, identifying outdated software, insecure accounts, and deprecated protocols. The remediation packages were prepared for submission to the Change Control Board (CAB). 

<details>
<summary>Click to expand meeting text</summary>

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst): Morning, how are you doing?

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team): Not bad for a Monday. And yourself?

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst): I'm still alive, so I can't complain. But before we get into the vulnerabilities, how did the actual scan go on your end? Did you have any outages or overutilization or anything?

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team): The scan went well. We were monitoring them, and aside from all the open connections, we would have never known a scan was taking place.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst): Yeah, that's good news. I kind of expected that much. We can keep monitoring going forward, but I don't expect we'll have any issues with resource utilization. Do you mind if I dive into the vulnerability findings?

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team): Yeah, absolutely.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst): Cool. I'm going to share my screen really quick. So basically, the majority of these vulnerabilities come from Wireshark being installed. You can see all these Wiresharks because it's just super out of date, that's all. One interesting thing I did find is that the local guest account on the servers actually belongs to a group, and I looked deeper, and it belongs to the local administrators group. I'm not sure why that is. Also, some of these might be automatically resolved by Windows updates, like this Microsoft Edge Chromium one. And then I'm not sure about this one as well; it could be resolved by Windows updates. I'm not really sure. But we don't have to worry about the self-signed certificate one because it's just the computer's self-signed certificate.

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team): Right.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst): But these medium-strength cipher suites and TLS 1.1 and 1.0 are deprecated cipher suites and deprecated protocols. So I think we should take some time to remediate these. Basically, just Wireshark the protocols, cipher suites, and removing the guest account is what we're looking at.

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team): Very interesting. The good news is I suspect most of our servers are going to have the same vulnerabilities. Hopefully, that makes things easier during remediation.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) Zack (Vulnerability Analyst): Yeah, that's actually good news—like a uniform loadout. Do you foresee any issues with remediating any, specifically like the cipher suites and the insecure protocols?

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) Jimmy (Server Team): I highly doubt there will be any issues. We'll run it through the next Change Control Board. Uninstalling Wireshark and fixing the guest account shouldn't be an issue; those aren't supposed to be on the servers anyway. I'll have to talk to our CIS admins about that.

</details>

---

### Step 9) Mock CAB Meeting: Implementing Remediations

The Change Control Board (CAB) reviewed and approved the plan to remove insecure protocols and cipher suites. The plan included a rollback script and a tiered deployment approach.  

<details>
<summary>Click to expand meeting text</summary>
    
![Brenda](https://github.com/user-attachments/assets/fc846433-bdd9-4cae-bf11-c7fca5f1bdb7) **Brenda (CAB Facilitator):** Okay, next up on the list are a couple of vulnerability remediations for the server team. Number one: removal of insecure protocols, and number two: removal of insecure Cipher Suites. It looks like Zack from the risk department is working in conjunction with Jimmy from infrastructure on this. Jimmy, do you want to walk us through the technical aspects of the change being implemented?

![Jimmy](https://github.com/user-attachments/assets/342408c8-2873-4fb3-ba99-ab70c5f1c352) **Jimmy (Server Team):** Normally I would, but do you mind giving this one to Zack? He actually built a solution for us, and we're still getting used to the process.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) **Zack (Vulnerability Analyst):** Uh, yeah, I can explain these. So basically, insecure Cipher Suites and protocols—the existence of those on the system just means that the system is capable of negotiating and using some kind of algorithm or protocol that's been deprecated. Right? If it connects to a server and the server only wants to use those protocols, it's possible that the computer will use them. These are controlled by the Windows registry. It's a really simple fix. We just wrote a PowerShell script that goes through and disables all the insecure protocols and ciphers, and then enables the ones that are standardized or that are like today's standard that are secure. So it's really straightforward.

![Samantha](https://github.com/user-attachments/assets/79938ccd-89fb-48ac-a053-3c7ec0d04f4f) **Samantha (Lead System Engineer):** Yeah, that sounds good. But what if something goes wrong? Do we have a rollback plan in place? Did you even think about that?

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) **Zack (Vulnerability Analyst):** Yes, absolutely. So first of all, we have a tiered deployment. That means a pilot group, which is a really small group of computers, pre-pilot, pre-production, and then finally production where it goes everywhere. On top of this, we have a fully built-in test and automated rollback script for each remediation. The script will actually restore the original protocols and ciphers should there be any unknown issues that come up.

![Samantha](https://github.com/user-attachments/assets/79938ccd-89fb-48ac-a053-3c7ec0d04f4f) **Samantha (Lead System Engineer):** That sounds good. I guess I notice the fixes are simple registry updates. I'm not too concerned, I suppose.

![Zack](https://github.com/user-attachments/assets/0d32b225-87b9-409e-83af-122c449ea81e) **Zack (Vulnerability Analyst):** Yep, exactly. Any more questions from anybody?

![Brenda](https://github.com/user-attachments/assets/fc846433-bdd9-4cae-bf11-c7fca5f1bdb7) **Brenda (CAB Facilitator):** Great! That wraps things up for this week's CAB meeting. See you all next week!

**All:** See you later!


</details>

---
### Step 10 ) Remediation Effort

#### Remediation Round 1: Outdated Wireshark Removal

The server team used a PowerShell script to remove outdated Wireshark. A follow-up scan confirmed successful remediation.  
[Wireshark Removal Script](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/remediation-wireshark-uninstall.ps1)  

<img width="634" alt="Scan 2" src="https://github.com/user-attachments/assets/54bfa051-e3c2-4bcd-b343-9dec58e0ee0f" />

[Scan 2 - Third Party Software Removal](https://drive.google.com/file/d/1hi0S02tM4LOKWCfEdPexCejsGUPnDCXm/view?usp=sharing)



#### Remediation Round 2: Insecure Protocols & Ciphers

The server team used PowerShell scripts to remediate insecure protocols and cipher suites. A follow-up scan verified successful remediation, and the results were saved for reference.  
[PowerShell: Insecure Protocols Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-protocols.ps1)
[PowerShell: Insecure Ciphers Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-cipher-suites.ps1)

<img width="630" alt="Scan 3" src="https://github.com/user-attachments/assets/ca70880a-fbb0-4a88-aa37-dd62d021bd5e" />

[Scan 3 - Ciphersuites and Protocols](https://drive.google.com/file/d/1VopbZlTPOaoLYJXHKo0VXtLTS7mW3XfH/view?usp=sharing)



#### Remediation Round 3: Guest Account Group Membership

The server team removed the guest account from the administrator group. A new scan confirmed remediation, and the results were exported for comparison.  
[PowerShell: Guest Account Group Membership Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-guest-local-administrators.ps1)  

<img width="627" alt="scan 4" src="https://github.com/user-attachments/assets/f964d285-77e9-4e07-ac5a-c0921688eaed" />

[Scan 4 - Guest Account Group Removal](https://drive.google.com/file/d/1OD1sBOrXVIRQ-hQd4cHTU8QBwdUpbY0i/view?usp=sharing)


#### Remediation Round 4: Windows OS Updates

Windows updates were re-enabled and applied until the system was fully up to date. A final scan verified the changes  

<img width="627" alt="scan 5" src="https://github.com/user-attachments/assets/6b4e80a8-f964-42cf-a526-9cc4477a20a4" />

[Scan 5 - Post Windows Updates](https://drive.google.com/file/d/19h6PeROIL7aLs3XeTgwKi-o0ixfe4AjR/view?usp=sharing)

---


### First Cycle Remediation Effort Summary

The remediation process reduced total vulnerabilities by 60%, from 31 to 13. Critical vulnerabilities were resolved by the second scan (100%), and high vulnerabilities dropped by 64% (11 to 4). Mediums were reduced by 53% (17 to 8). Interestingly, Windows Update created a new vulnerability as shown in Scan 5 (SMB Signing Not Required) rather than remediate one. In an actual production environment, asset criticality would further guide future remediation efforts.  

<img width="1920" alt="remediation data" src="https://github.com/user-attachments/assets/60bcdbfc-34be-462b-afa2-b6f99b2c202f" />

[Remediation Data](https://docs.google.com/spreadsheets/d/1_WdvoIN4H0syXYXncAg-MpmSADD2lW1LJzZZKkJ4Dp8/edit?gid=0#gid=0)


---

### On-going Vulnerability Management (Maintenance Mode)

After completing the initial remediation cycle, the vulnerability management program transitions into **Maintenance Mode**. This phase ensures that vulnerabilities continue to be managed proactively, keeping systems secure over time. Regular scans, continuous monitoring, and timely remediation are crucial components of this phase. (See [Finalized Policy](https://docs.google.com/document/d/1rvueLX_71pOR8ldN9zVW9r_zLzDQxVsnSUtNar8ftdg/edit?usp=drive_link) for scanning and remediation cadence requirements.)

Key activities in Maintenance Mode include:
- **Scheduled Vulnerability Scans**: Perform regular scans (e.g., weekly or monthly) to detect new vulnerabilities as systems evolve.
- **Patch Management**: Continuously apply security patches and updates, ensuring no critical vulnerabilities remain unpatched.
- **Remediation Follow-ups**: Address newly identified vulnerabilities promptly, prioritizing based on risk and impact.
- **Policy Review and Updates**: Periodically review the Vulnerability Management Policy to ensure it aligns with the latest security best practices and organizational needs.
- **Audit and Compliance**: Conduct internal audits to ensure compliance with the vulnerability management policy and external regulations.
- **Ongoing Communication with Stakeholders**: Maintain open communication with teams responsible for remediation, ensuring efficient coordination.

By maintaining an active vulnerability management process, organizations can stay ahead of emerging threats and ensure long-term security resilience.
