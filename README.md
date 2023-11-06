# EX 3:SubQueries, Views and Joins
## DATE:17/8/23
## Create employee Table
```
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```
## Create department table
```
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
Insert the values in the department table
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```
## Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.
## QUERY:
```
CREATE VIEW details AS SELECT ENAME FROM EMP WHERE SALARY >(select SALARY from EMP where EMPNO=7566);
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/1aa53478-3c79-4d6b-a40d-cea96e4690f9)


## Q2) List the ename,job,sal of the employee who get minimum salary in the company.
## QUERY:
```
 CREATE VIEW minimum AS select ENAME,JOB,SALARY from EMP where SALARY =(select MIN(SALARY) from EMP);
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/10df78b4-1a54-4024-b637-3a09b39efd81)


## Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.
## QUERY:
```
select ENAME,JOB from EMP where  DEPTNO=10 AND JOB='SALESMAN';
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/2bb3ffb0-5552-49a4-9f90-c00f3531973c)


## Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.
## QUERY:
```
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/60de6359-18dd-452c-b5f6-ef37d9935734)


## Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.
## QUERY:
```
create view empv30 AS select EMPNO,ENAME,SALARY from EMP where DEPTNO=30;
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/493801ec-94a9-4ed0-aa44-0b1ac2be0f7a)


## Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table
## QUERY:
```
update EMP set SALARY=SALARY*1.1 WHERE JOB='clerk';

create view empv5 as select EMPNO,ENAME,SALARY,JOB from EMP;
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/4ae0a2ca-e437-4620-99a3-17c44b3d8533)

## Create a Customer1 Table
```
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
## Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
## QUERY:
```
select s.name,c.cust_name,s.city from salesman1 as s ,customer1 as c where s.city=c.city;
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/60e6a05c-f128-4c10-ab68-2baa8b8eb55e)


## Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.
## QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 as s inner join customer1 as c on s.city=c.city where s.commission>0.13;
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/e3bdc796-9b74-4c98-9bc9-1badee641ac7)


## Q9) Perform Natural join on both tables
## QUERY:
```
 select s.name,c.cust_name,c.city,s.commission from salesman1 as s natural join customer1 as c where s.commission>0.13;
```
## OUTPUT:
![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/9ff3d3aa-5a0d-47b8-af5e-614708db380f)

## Q10) Perform Left and right join on both tables
## QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 as s left join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;

select s.name,c.cust_name,c.city,s.commission from salesman1 as s right join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;
```
## OUTPUT:

![image](https://github.com/vikashsenthil21/EX-3-SubQueries-Views-and-Joins/assets/119433834/25bc4183-f857-49ae-9c41-0aa548fab6e0)

## RESULT:
Hence successfully created a manager database and execute DML queries using SQL.
