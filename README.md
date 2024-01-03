# 3-Tier-Infra-Project
3 Tier E-commerce Architecture
This architecture supports building a scalable e commerce platform that needs to handle varying levels of traffic based on customer demand. Here's an overview of how the architecture could be utilized:

## 3 Tier E-commerce Architecture
1) ###### Route 53 for DNS Resolution:
    I used Amazon's Route 53 to manage and resolve domain names for the e commerce platform. This includes mapping user-friendly domain names to the corresponding AWS resources, such as the ALB.

2) ###### Front-End Servers in Auto-Scaling Group with Application Load Balancer (ALB):
    The front-end servers are responsible for serving the user Interface of the e-commerce website, and they are deployed within an Auto Scaling Group to automatically adjust to changes In demand.
    The application Load Balancer (ALB) Is used to distribute Incoming traffic across multiple front-end servers, ensuring high availability and load balancing.

3) ###### Public Subnets, Route Tables, and Internet Gateway for Front-End Servers:    


4) ###### Web Application Servers in Auto-Scaling Group:
    The web application servers, where the core business logic of the e commerce platform resides, are also set up in an Auto Scaling Group to handle Varying workloads.
    These servers are connected to a Relational Database instance using security groups. The RDS instance uses the MySOL engine, providing a scalable and managed database solution.

5) ###### Standby RDS MySQL Instance in Availability Zone 1b:
    To enhance the avallability and fault tolerance of the database, I deployed a standby RDS MySQL Instance In a different availability zone (1b). This ensures that If there's a fallure in one avallability zone, the standby instance in the other zone can take over seamlessly by being promoted to become the master.

6) ###### NAT Instances for Private App Servers:
    NAT (Network Address Translation) instances are deployed in availability zones (1a and 1b) to allow private application servers in the backend to access the internet for updates and fetching packages while maintaining a secure and controlled environment.
    
    This architecture ensures that the e commerce platform is highly available, scalable, and resilient to failures. The combination of auto-scaling groups, load balancing, multi-AZ database deployment, and networking components allows the infrastructure to efficiently handle varying levels of traffic while providing a reliable and responsive user experience