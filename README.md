Consider the Employee table and write SQL command to get the following.
Create Table Statement

CREATE TABLE Empl (
    Empno INT PRIMARY KEY,
    ename VARCHAR(50),
    job VARCHAR(50),
    mgr INT,
    hiredate DATE,
    sal INT,
    comm INT,
    deptno INT
);
Insert Sample Data (optional, based on your provided data)

INSERT INTO Empl VALUES
(8369, 'SMITH', 'CLERK', 8902, '1990-12-18', 800, NULL, 20),
(8499, 'ANYA', 'SALESMAN', 8698, '1991-02-20', 1600, 300, 30),
(8521, 'SETH', 'SALESMAN', 8698, '1991-02-22', 1250, 500, 30),
(8566, 'MEHADEVAN', 'MANAGER', 8839, '1991-04-02', 2985, NULL, 20),
(8654, 'MOMIN', 'SALESMAN', 8698, '1991-09-28', 1250, 1400, 30),
(8698, 'BINA', 'MANAGER', 8839, '1991-05-01', 2850, NULL, 30),
(8882, 'SHIVANSH', 'MANAGER', 8839, '1991-06-09', 2450, NULL, 10),
(8888, 'SCOTT', 'ANALYST', 8566, '1992-12-09', 3000, NULL, 20),
(8839, 'AMIR', 'PRESIDENT', NULL, '1991-11-18', 5000, NULL, 10),
(8844, 'KULDEEP', 'SALESMAN', 8698, '1991-09-08', 1500, 0, 30);
A. Write a query to display EName and Sal of employees whose salary are greater than or equal to 2200?

SELECT ename, sal
FROM employees
WHERE sal >= 2200;
B. Display details of employees who are not getting commission

SELECT *
FROM employees
WHERE comm IS NULL;
C. Display employee name and salary of those employees who don’t have their salary in the range of 2500 to 4000

SELECT ename, sal
FROM employees
WHERE sal NOT BETWEEN 2500 AND 4000;
D. Display the name, job title and salary of employees who don’t have a manager

SELECT ename, job, sal
FROM employees
WHERE mgr IS NULL;
E. Write a query to display the name of an employee whose name contains “A” as third alphabet?

SELECT ename
FROM employees
WHERE ename LIKE '%T';
2.) Write a a program for JDBC to connectivity and insert the below data.

CREATE TABLE employee (
    empcode INT PRIMARY KEY,
    empname VARCHAR(50),
    empage INT,
    esalary INT
);
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class JdbcInsertExample {

    public static void main(String[] args) {

        // Database credentials and URL
        String jdbcURL = "jdbc:mysql://localhost:3306/testdb";  // Change if needed
        String username = "root";  // Your DB username
        String password = "password";  // Your DB password

        // SQL Insert statement
        String sql = "INSERT INTO employee (empcode, empname, empage, esalary) VALUES (?, ?, ?, ?)";

        // Employee data to insert
        Object[][] employees = {
            {101, "Jenny", 25, 10000},
            {102, "Jacky", 30, 20000},
            {103, "Joe", 20, 40000},
            {104, "John", 40, 80000},
            {105, "Shameer", 25, 90000}
        };

        try (Connection conn = DriverManager.getConnection(jdbcURL, username, password);
             PreparedStatement pstmt = conn.prepareStatement(sql)) {

            for (Object[] emp : employees) {
                pstmt.setInt(1, (int) emp[0]);
                pstmt.setString(2, (String) emp[1]);
                pstmt.setInt(3, (int) emp[2]);
                pstmt.setInt(4, (int) emp[3]);

                pstmt.executeUpdate();
            }

            System.out.println("Records inserted successfully!");

        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}


ABISHEK ABISHEK
