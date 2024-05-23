# Practice3
1.
CREATE DATABASE "Company" \
    WITH \
    OWNER = postgres \
    ENCODING = 'UTF8' \
    CONNECTION LIMIT = -1 \
    IS_TEMPLATE = False; 

CREATE TABLE Projects ( \
 id int primary key , \
	project_name varchar 
	
) 

CREATE TABLE Departments ( \
 id int primary key , \
	department_name varchar 
	
) 
 \
CREATE TABLE Employees ( \
 id int primary key , \
	first_name varchar, \
	last_name varchar,  \
	project_id int NOT NULL REFERENCES Projects(id), \
	department_id int NOT NULL REFERENCES Departments(id) 
	
) 
2.
INSERT INTO projects(id, project_name) VALUES \
(1, 'Food delivery'),  \
(2, 'Furniture Delivery'),  \
(3, 'Software delivery') \
 \
INSERT INTO departments(id, department_name) VALUES \
(1, 'IT'),  \
(2, 'Management'),  \
(3, 'Creative Department') 
 
INSERT INTO employees(id, first_name, last_name, department_id, project_id) VALUES \
(1, 'Robert', 'Smith', 1, 2),  \
(2, 'Alice', 'Johnson', 2, 3), \
(3, 'Nicholas', 'Cage', 3, 3), \
(4, 'Bobert', 'Robertson', 2, 1), \
(5, 'Maria', 'Tereza', 1, 1) 

3.SELECT * FROM employees WHERE department_id = 1 

4. UPDATE employees SET first_name='Robert' WHERE id = 1 

5. DELETE FROM employees WHERE project_id = 2; \
DELETE FROM projects WHERE id = 2 

6.CREATE INDEX last_name_idx ON employees(last_name) 

7.SELECT departments.department_name, COUNT(*) AS employee_number  \
FROM employees  \
JOIN departments ON employees.department_id = departments.id \
GROUP BY departments.department_name; 

8. SELECT first_name, last_name, department_name \
FROM employees  \
JOIN departments ON employees.department_id = departments.id 

9.BEGIN; 

INSERT INTO departments(id, department_name) VALUES \
(4, 'Customer support'); \
INSERT INTO projects(id, project_name) VALUES \
(4, 'Health monitor'); \
COMMIT; \
10.  \
В pgadmin4 нажать правой кнопкой мыши на company->backup->выбрать каталог. \
TRUNCATE employees \
В pgadmin4 нажать правой кнопкой мыши на company->restore->выбрать файл. 
